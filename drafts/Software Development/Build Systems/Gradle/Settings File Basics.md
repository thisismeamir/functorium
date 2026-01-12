---
sticker: lucide//atom
---
# Settings File Basics
## Overview
The settings file is the entry point of every Gradle project.
![[Pasted image 20250813185057.png]]
## Development
The primary purpose of the settings file is to define the project structure, usually by naming the root project, and adding the subprojects. 

> [!IMPORTANT] In single project builds the `settings.gradle` file is optional. While in multi-project builds it's mandatory and declares all the sub-projects.

The settings file is typically located at the root folder of the project. Without a settings file in the root project, Gradle considers the build to be a single project by default.

Let's take a look at a typical settings file:
```kotlin
rootProject.name = "root-project"   

include("sub-project-a")            
include("sub-project-b")
include("sub-project-c")
```
1. `rootProject.name`: Defines the name of the main project
2. `include("...")`: Declares to Gradle existing sub-projects.


## Morphisms
- Depends on
- Is included in
- Refined by
- Is Equivalence to

## Tags
#atom #theory 