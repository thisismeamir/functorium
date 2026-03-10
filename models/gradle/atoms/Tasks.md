---
sticker: lucide//atom
---
# Tasks

![[../../../attachments/Pasted image 20250815193747.png]]
A task represents some **independent unit of work** that a build performs, such as compiling classes, creating a JAR, generating Javadoc, or publishing archives to a repository.

Tasks are the building blocks of every Gradle build.

Common types of tasks include:

- Compiling source code
- Running tests
- Packaging output (e.g., creating a JAR or APK)
- Generating documentation (e.g., Javadoc)
- Publishing build artifacts to repositories

Each task is independent but can depend on other tasks to run first. Gradle uses this information to figure out the most efficient order to execute tasks — skipping anything that’s already up to date.

## Running Tasks
To run a task simply use the wrapper to followed by the task name:

```bash
./gradlew taskName
```

To list all available tasks use:
```bash
./gradlew tasks
```
which would be followed by a response like:
```text
Application tasks
-----------------
run - Runs this project as a JVM application

Build tasks
-----------
assemble - Assembles the outputs of this project.
build - Assembles and tests this project.

...

Documentation tasks
-------------------
javadoc - Generates Javadoc API documentation for the main source code.

...

Other tasks
-----------
compileJava - Compiles main Java source.

...
```
### Task Dependencies
Most tasks require specific tasks to be run before them, this is a task dependency. Gradle knows automatically when you request a task, that it has to run the dependencies first.

As an example
```
$ ./gradlew build

> Task :app:compileJava
> Task :app:processResources NO-SOURCE
> Task :app:classes
> Task :app:jar
> Task :app:startScripts
> Task :app:distTar
> Task :app:distZip
> Task :app:assemble
> Task :app:check
> Task :app:build

BUILD SUCCESSFUL in 764ms
7 actionable tasks: 7 executed
```
