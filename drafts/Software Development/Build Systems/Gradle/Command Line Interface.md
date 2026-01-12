---
sticker: lucide//atom
---
I# Command Line Interface
## Overview
Gradle command line interface is a system-installed version on Gradle on computer. It is recommended to use the wrapper instead. The information regarding the wrapper is provided[^1].
## Development
### Running Commands
To execute a Gradle command we would remember this simple structure:
```bash
gradle [taskName...] [--option-name...]
```
You can specify more tasks by introducing them separated by space:
```bash
gradle [taskName1 taskName2...] [--option-name...]
```
For example, to run a task named `build`
```bash
gradle build
```
To first clean and then build
```bash
gradle clean build
```
### Options
Options can appear in the command enhancing the behavior of the task:
```bash
gradle [--option-name...] [taskName...]
```
For options that accept a value assign them using `=` operator:
```bash
gradle [...] --console=plain
```
Some options are toggles and have opposite forms:
```bash
gradle build --build-cache
gradle build --no-build-cache
```
It also provides short options for some options:
```bash
gradle --help
gradle -h
```
### Executing Tasks
In Gradle tasks belong to specific projects, to run a task that belongs to the root project we write:
```bash
gradle :taskName
```
and for subprojects:
```bash
gradle :subproject:taskName
```
If you run a task without colon, Gradle would run the task according to the current directory:
```bash
gradle taskName
```
Again some tasks might accept options, for which, we use `--` prefix.
## Morphisms
- Depends on
- Is included in
- Refined by
- Is Equivalence to

## Tags
#atom #theory 

[^1]: [[Wrapper]]
