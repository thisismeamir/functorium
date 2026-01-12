---
sticker: lucide//atom
---
# Project Structure
The presence of the `gradlew` and `gradlew.bat` ensures 
```text
project
## Where Gradle stores wrapper files and more
├── gradle   
## Gradle version catalog for dependency management
│   ├── libs.versions.toml              
│   └── wrapper
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
## Gradle wrapper scripts
├── gradlew                         
├── gradlew.bat                
## Gradle settings file to define a root project name and subproject and more.
├── settings.gradle(.kts)
## Each Gradle sub project contains a build.gradle script/
├── subproject-a
│   ├── build.gradle(.kts)              
│   └── src                         
└── subproject-b
    ├── build.gradle(.kts)              
    └── src                         
```

## Morphisms
- Depends on
- Is included in
- Refined by
- Is Equivalence to

## Tags
#atom #theory 