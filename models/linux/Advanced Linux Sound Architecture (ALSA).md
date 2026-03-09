---
sticker: lucide//hash
---
# Advanced Linux Sound Architecture

## Installation 

The Advanced Linux Sound Architecture (ALSA) provides kernel driven sound card drivers. It replaces the original Open Sound System (OSS).

Besides the sound device drivers, ALSA also bundles a user space driven library for application developers. They can then use those ALSA drivers for high level API development. This enables direct (kernel) interaction with sound devices through ALSA libraries

> [!NOTE]
    > An explanation of ALSA related terminology—_interface_, _card_, _device_ (a _card_ is not a _device_), _subdevice_, and more—can be found on [Wikipedia:Advanced Linux Sound Architecture#Concepts](https://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture#Concepts "wikipedia:Advanced Linux Sound Architecture").

### Firmware

The [Sound Open Firmware](https://www.sofproject.org/) (SOF) ([sof-firmware](https://archlinux.org/packages/?name=sof-firmware)) is usually required for laptops—they tend to utilize Cadence Tensilica Xtensa architecture [DSPs](https://en.wikipedia.org/wiki/Digital_signal_processor "wikipedia:Digital signal processor"), see the list of the [supported platforms](https://thesofproject.github.io/latest/platforms/). In case of the missing firmware the [journal](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Journal "Journal") will provide messages such as:

```
error: sof firmware file is missing
error: failed to load DSP firmware -2
error: sof_probe_work failed err: -2
```

For more SOF troubleshooting information, see [Overview of Intel hardware platforms](https://thesofproject.github.io/latest/getting_started/intel_debug/introduction.html).

The [linux-firmware-cirrus](https://archlinux.org/packages/?name=linux-firmware-cirrus) package is needed for laptops with Cirrus Logic [smart amplifiers](https://www.cirrus.com/products/audio/boosted-amplifiers/laptop-audio). See also:

- [Audio drivers for Cirrus Logic CS35L54/56/57/63 Boosted Smart Amplifiers](https://docs.kernel.org/sound/codecs/cs35l56.html),
- [archlinux/packaging/packages/linux-firmware#19](https://gitlab.archlinux.org/archlinux/packaging/packages/linux-firmware/-/issues/19).

The [linux-firmware-intel](https://archlinux.org/packages/?name=linux-firmware-intel) package is needed for some Intel audio devices.

The [alsa-firmware](https://archlinux.org/packages/?name=alsa-firmware) package contains firmware that may be required for [certain](https://github.com/alsa-project/alsa-firmware) sound cards.

See also [#Cards and modules](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Advanced_Linux_Sound_Architecture#Cards_and_modules) and [Linux firmware](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Linux_firmware "Linux firmware").

### ALSA utilities

[Install](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Install "Install") the [alsa-utils](https://archlinux.org/packages/?name=alsa-utils) package. This contains (among other utilities) the [alsamixer(1)](https://man.archlinux.org/man/alsamixer.1) and [amixer(1)](https://man.archlinux.org/man/amixer.1) utilities. `amixer` is a shell command to change audio settings, while `alsamixer` provides a more intuitive [ncurses](https://en.wikipedia.org/wiki/Ncurses "wikipedia:Ncurses") based interface for audio device configuration.

### ALSA and `systemd`

The [alsa-utils](https://archlinux.org/packages/?name=alsa-utils) package comes with [systemd](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Systemd "Systemd") unit configuration files `alsa-restore.service` and `alsa-state.service` by default.

These are automatically installed and activated during installation (via package provided `symlink` to [sound.target](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Systemd#Targets "Systemd")). The options are as follows:

- `alsa-restore.service` reads `/var/lib/alsa/asound.state` on boot and writes updated values on shutdown, provided `/etc/alsa/state-daemon.conf` does not exist. As `/etc/alsa/state-daemon.conf` is not created without a conscious action of the user, it is the default method.
- `alsa-state.service` (Re-)Starts `alsactl` in daemon mode to continuously keep track of, and persist, volume changes, under the condition that the user has consciously created `/etc/alsa/state-daemon.conf`.

Evidently, both methods are mutually exclusive. You can decide for one of the two approaches depending on your requirements. To edit these units, see [systemd#Editing provided units](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Systemd#Editing_provided_units "Systemd"). You can check their status using [systemctl](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Systemctl "Systemctl").

For further information, see [alsactl(1)](https://man.archlinux.org/man/alsactl.1).

## Unmuting the channels

By default, ALSA has all channels muted. Those have to be unmuted manually.

### Unmute with amixer

Unmuting the sound card's master volume can be done by using _amixer_:

```
$ amixer sset Master unmute
$ amixer sset Speaker unmute
$ amixer sset Headphone unmute
```

### Unmute with `alsamixer`

Unmuting the sound card can be done using `alsamixer`:

```
$ alsamixer
```
The `MM` label below a channel indicates that the channel is muted, and `OO` indicates that it is open.

Scroll to the `Master` and `PCM` channels with the `Left` and `Right` keys and unmute them by pressing the `m` key.

Use the `Up` key to increase the volume and obtain a value of `0` dB gain. The gain can be found in the upper left next to the `Item:` field.

**Note**If gain is set above 0 dB, audible distortion can become present.

### Unmute 5.1/7.1 sound

To get full [5.1](https://en.wikipedia.org/wiki/5.1_surround_sound "wikipedia:5.1 surround sound") or [7.1 surround sound](https://en.wikipedia.org/wiki/7.1_surround_sound "wikipedia:7.1 surround sound"), you will likely need to unmute other channels such as `Front`, `Surround`, `Center`, `LFE` (subwoofer) and `Side`. (Those are channel names with [Intel HD Audio](https://en.wikipedia.org/wiki/Intel_High_Definition_Audio "wikipedia:Intel High Definition Audio"); they may vary with different hardware)

**Note**Please take note that this will not automatically upmix stereo sources (like most music). In order to accomplish that, see [#Upmixing](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Advanced_Linux_Sound_Architecture#Upmixing).

### Enable the microphone

To enable your microphone, switch to the Capture tab with `F4` and enable a channel with `Space`. See [/Troubleshooting#Microphone](zim://8b867366-dd5f-67fc-895c-c6ab3638d6a3.zim/Advanced_Linux_Sound_Architecture/Troubleshooting#Microphone "Advanced Linux Sound Architecture/Troubleshooting") if microphone does not work.

### Test your changes

Next, test to see if sound works:

$ speaker-test -c 2

Change `-c` to fit your speaker setup. Use `-c 8` for 7.1, for instance:

$ speaker-test -c 8

If audio is being outputted to the wrong device, try manually specifying it with the argument `-D`.

$ speaker-test -D default:PCH -c 8

`-D` accepts PCM channel names as values, which can be retrieved by running the following:

$ aplay -L | grep :CARD

default:CARD=PCH  # 'default:PCH' is the PCM channel name for -D
sysdefault:CARD=PCH
front:CARD=PCH,DEV=0
surround21:CARD=PCH,DEV=0
surround40:CARD=PCH,DEV=0
surround41:CARD=PCH,DEV=0
surround50:CARD=PCH,DEV=0
surround51:CARD=PCH,DEV=0
surround71:CARD=PCH,DEV=0

### Additional notes

- If your system has more than one soundcard, then you can switch between them by pressing `F6`

- Some cards need to have digital output muted or disabled in order to hear analog sound and vice versa.

- Some machines, like the Thinkpad T61, have a `Speaker` channel which must be unmuted and adjusted as well.

- Some machines, like the Dell E6400, may also require the `Front` and `Headphone` channels to be unmuted and adjusted.

- If your volume adjustments seem to be lost after you reboot, try running _alsamixer_ as root.