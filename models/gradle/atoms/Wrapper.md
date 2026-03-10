---
sticker: lucide//atom
---
	# Wrapper
## Overview
Gradle wrapper is the means of invoking Gradle.
![[../../../attachments/Pasted image 20250813181023.png]]
## Development
The script invokes a declared version of Gradle, downloading it before hand if necessary..
![[../../../attachments/Pasted image 20250813181127.png]]
In every Gradle project two files (one for Unix machines and one for Windows) is available. those are `gradle` and `gradle.bat`. If a project doesn't have these files, it's possible that the project is not a Gradle project at all (although it might be that Gradle wrapper is not set up on the project. 


> [!IMPORTANT] Note
> The wrapper is note something that you would download from the internet. It's only to be accessible through running `gradle wrapper` on a computer that has Gradle CLI installed already.

### Wrapper Advantages
The wrapper provides multiple advantages:
1. Automatically downloads and uses a specific version of Gradle.
2. Standardize a project for a specific version of Gradle.
3. Provisions the same Gradle version for different users and environments.
4. Makes it easy to use Gradle build projects without installing Gradle on the system.

### Using the Wrapper
It's important to make difference between the two ways we run Gradle.
1. `gradle` command on a computer that has Gradle CLI installed on it.
2. Using the Gradle wrapper by running `./gradlew` or `./gradlew.bat` in the root folder of the project.
The Gradle wrapper is recommended to make sure that the advantages of using the wrapper holds. We would use the command:

```bash
./gradlew build
```
### Understanding the Wrapper files:
```text
.
├── gradle
│   └── wrapper
│       ├── gradle-wrapper.jar  
│       └── gradle-wrapper.properties   
├── gradlew 
└── gradlew.bat 
```
1. `gradle-wrapper.jar`: This is a small JAR file that contains Gradle Wrapper code. It is responsible for downloading and installing the correct version of Gradle.
2. `gradle-wrapper.properties`: This is a properties file that provides some context for the wrapper. For example the url to download Gradle from and a zip file of the Gradle distribution.

> [!DANGER] Do not alter these files
> If you wish to change the version of the Gradle in the project or just look at it consider running `./gradlew --version` for checking on the version and `./gradlew wrapper --gradle-version <version-number>` for changing the version.

