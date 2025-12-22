# cern.sh What This Script Does — Explained Simply
before starting in your linux shell go to the script directory and type:
```bash
chmod +x cern.sh
```

so that you can run it as a script.


This script (named **cern.sh**) is a small tool that helps you work with **CERN’s computers**, especially the lxplus system, **without needing to type long or complicated commands**.

Instead of remembering many different commands, you simply type:

```
cern login
```

or

```
cern jupyter
```

and the script does all the complicated work for you.

It is basically a **shortcut tool** that makes your daily CERN tasks easier.

---

# You MUST Change Your Username

At the top of the script, you will see something like this:

```bash
CERN_USER="amirhoss"
CERN_HOST="lxplus.cern.ch"
CERN_REMOTE_PATH="/afs/cern.ch/user/a/amirhoss"
```

You MUST replace **amirhoss** with **your own CERN username**.

For example, if your CERN username is `mohseni`, change it to:

```bash
CERN_USER="mohseni"
CERN_REMOTE_PATH="/afs/cern.ch/user/m/mohseni"
```

The letter after `/user/` should be the **first letter of your username**.

If you don’t change this, the script won't work for your account.

---

# What Commands This Script Gives You

Once installed, you can use the command `cern` followed by an action.

### 1. Login to CERN servers

```
cern login
```

Connects you to lxplus securely.

---

### 2. Open Jupyter Notebook or Lab from CERN on your own browser

```
cern jupyter
```

The script creates a secure tunnel so your local browser can open CERN’s Jupyter service.

---

### 3. Send your files to CERN (upload)

```
cern push
```

### 4. Download your files from CERN (retrieve)

```
cern pull
```

These work like simple “send” and “receive” buttons for your files.

---

### 5. Create a backup of your CERN files

```
cern backup
```

---

### 6. Mount your CERN home folder on your computer

(so you can open it like a normal folder)

```
cern mount
```

---

### 7. Unmount it

```
cern umount
```

---

### 8. See all available commands

```
cern help
```

---

# How to Install and Use It

### 1. Save the script

Place the file `cern.sh` somewhere like:

```
~/bin/cern.sh
```

### 2. Make it executable

Open your terminal and run:

```
chmod +x ~/bin/cern.sh
```

### 3. Create a shortcut command

Add this line to your `.bashrc` or `.zshrc`:

```
alias cern="$HOME/bin/cern.sh"
```

Then reload your shell or open a new terminal.

### 4. Use it

You can now run commands like:

```
cern login
cern push
cern jupyter
```
# cern.sh — Technical Documentation

## Overview

`cern.sh` is a Bash helper script designed to simplify routine interactions with CERN computing services, primarily LXPLUS and AFS.  
It provides a unified command interface (`cern <command>`) for:

- SSH access
- File synchronization (push/pull)
- Remote Jupyter tunneling
- AFS mounting
- Backups
- Misc runtime utilities

The script wraps common `ssh`, `rsync`, and `sshfs` patterns into well-defined subcommands, improving usability and reducing operational overhead.
## Configuration Variables

These variables must be configured per user:

```bash
CERN_USER="your-username"
CERN_HOST="lxplus.cern.ch"
CERN_REMOTE_PATH="/afs/cern.ch/user/x/your-username"
LOCAL_MOUNT="$HOME/cern_mount"
LOCAL_BACKUP="$HOME/cern_backup"
```

Explanation:
- `CERN_USER`  
    CERN account username.
- `CERN_HOST`  
    Remote entry-point host (default: lxplus).
- `CERN_REMOTE_PATH`  
    AFS home directory.  
    Convention: `/afs/cern.ch/user/<first-letter>/<username>`.
- `LOCAL_MOUNT`  
    Local directory used for remote mount via sshfs.
- `LOCAL_BACKUP`  
    Local directory used to store backups.

## Command Structure

Script invocation pattern:

```
cern <command> [options]
```

All subcommands are implemented inside functions and dispatched through a final `case` block.
## Subcommand Reference

### 1. `login`

SSH into LXPLUS with sane defaults.

Command:

```
cern login
```

Implementation summary:
- Uses `ssh -Y` or `ssh` depending on graphical needs.
- Configurable for agent forwarding or multiplexing if desired.
- Returns non-zero on failure.

---

### 2. `jupyter`

Create an SSH tunnel and forward a remote Jupyter service to a local port.

Command:

```
cern jupyter
```

Behavior:
- Allocates a local port (default: 8888).
- Sets up an SSH tunnel:
```
    ssh -L <localport>:localhost:<remoteport> ...
    ```
- Prints a URL that the user can open in their browser.
Assumes a running Jupyter instance on the CERN side, or instructs the user how to start one.
### 3. `push`
Synchronize local directory → CERN AFS.
Command:
```
cern push
```
Implementation details:

- Uses rsync with flags:  
    `-avz --delete`  
    to maintain an exact mirror.
- Local source defaults to current directory unless specified.
- Remote target:  
    `${CERN_USER}@${CERN_HOST}:${CERN_REMOTE_PATH}`
### 4. `pull`

Synchronize CERN AFS → local directory.
Command:
```
cern pull
```
Mirrors `push` but in reverse direction.
Used for retrieving work sessions, logs, notebooks, or batch job outputs.


### 5. `backup`
Creates a timestamped local backup of the CERN AFS home directory.
Command:
```
cern backup
```

Features:
- Ensures `LOCAL_BACKUP` exists.
- Stores incremental snapshots.
- Uses `rsync` with:
```
    --link-dest
    ```
    to minimize storage use.
### 6. `mount`
Mounts CERN AFS directory via `sshfs`.
Command:
```
cern mount
```
Workflow:
- Ensures `LOCAL_MOUNT` exists.
- Runs:
```
    sshfs ${CERN_USER}@${CERN_HOST}:${CERN_REMOTE_PATH} $LOCAL_MOUNT
    ```
- Allows direct browsing/editing of remote files as if local.
### 7. `umount`
Unmount the AFS mount.
Command:
```
cern umount
```
Executes:
```
fusermount -u $LOCAL_MOUNT
```
Handles stale mounts gracefully.
### 8. `help`

Displays usage information and command descriptions.
Command:
```
cern help
```

## Internal Structure

Common pattern inside script:
1. **Defaults and user configuration**  
    Declared at the top.
2. **Utility functions**  
    Examples:
    - Port checking
    - Error printing
    - Directory initialization
    - Wrapper around SSH commands
3. **Command functions**  
    Each subcommand is implemented as a function:
```
    cmd_login() { ... }
    cmd_push() { ... }
    cmd_mount() { ... }
    ```
    Each is self-contained and returns an exit code.
    
4. **Dispatcher**  
    At the end:
```bash
    case "$1" in
        login) cmd_login ;;
        push) cmd_push ;;
        …
        *) cmd_help ;;
    esac
    ```

This ensures clean structure and extensibility.

---

## Error Handling

- Functions return non-zero exit codes on failure.
- Errors are surfaced using a helper (if provided) or via `echo` + `exit 1`.
- Mount and tunnel operations include basic sanity checks:  
    _(directory exists, mount point empty, port available, ssh reachable)_

---

## Requirements

- Bash
- ssh
- rsync
- sshfs (optional, required for mount)
- fusermount (for unmount)

Optional:

- A working SSH key setup for passwordless authentication
- CERN 2FA if needed (script works with standard 2FA flow)

---

## Extending the Script

To add new commands:

1. Define a function:
```bash
    cmd_newfeature() {
        # logic
    }
    ```
    
1. Add it to the dispatcher:
```bash
    newfeature) cmd_newfeature ;;
    ```
2. Document it in the `help` function.    

The codebase is intentionally simple and modular.

---

## Recommended Improvements (Future Work)

- Auto-detection of username from SSH config
- Auto-starting Jupyter if not running
- Parallel backup option
- Logging support with timestamps
- Persistent SSH multiplexing socket
- Dry-run mode for push/pull
- Optional config file: `~/.cernrc`