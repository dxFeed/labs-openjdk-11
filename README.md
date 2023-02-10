Welcome to LabsJDK CE 11.

The latest release is available at https://github.com/graalvm/labs-openjdk-11/releases/latest

This is a fork of https://github.com/openjdk/jdk11u-dev (which is a read-only
mirror of https://hg.openjdk.java.net/jdk-updates/jdk11u-dev/) that
exists for the purpose of building a base JDK upon which GraalVM CE 11 is built.

It can be built with:
```
python build_labsjdk.py
```
This will produce a labsjdk installation under `build/labsjdks/release` along with 2 archives in the same
directory; one for the JDK itself and a separate one for the debug symbols.

You can pass extra options to the `configure` script using `--configure-option` or `--configure-options`. For example:
```
--configure-option=--disable-warnings-as-errors --configure-option=--with-extra-cxxflags=-fcommon --configure-option=--with-extra-cflags=-fcommon
```
or alternatively:
```
--configure-options=my.config
```
where the contents of the file `my.config` are:
```
--disable-warnings-as-errors
--with-extra-cxxflags=-fcommon
--with-extra-cflags=-fcommon
```

You can verify the labsjdk build with:
```
./build/labsjdks/release/java_home/bin/java -version
```

The original JDK README is [here](README).
Further information on building JDK 11 is [here](doc/building.md).

### Build instruction for Mac
1. Clone this repo and add oracle origin: https://github.com/graalvm/labs-openjdk-11.git
<img width="406" alt="image" src="https://user-images.githubusercontent.com/4503006/217626101-762b201e-f30d-4563-9961-a49fddd995c1.png">



_**Current release:**_ https://github.com/graalvm/graalvm-ce-builds/releases/tag/vm-22.3.1
```
Andrey.Mikhalev@UNIT-1738 Downloads % ./graalvm-ce-java11-22.3.1/Contents/Home/bin/java --version
openjdk 11.0.18 2023-01-17
OpenJDK Runtime Environment GraalVM CE 22.3.1 (build 11.0.18+10-jvmci-22.3-b13)
OpenJDK 64-Bit Server VM GraalVM CE 22.3.1 (build 11.0.18+10-jvmci-22.3-b13, mixed mode, sharing)
```
So we have to build _JVMCI_VERSION_ = **22.3-b13**
```
cd labs-openjdk-11
export JAVA_HOME=/Users/Andrey.Mikhalev/Downloads/graalvm-ce-java11-22.3.1/Contents/Home
python3 build_labsjdk.py --jvmci-version 22.3-b13 --configure-option=--disable-warnings-as-errors



Andrey.Mikhalev@UNIT-1738 labs-openjdk-11 % ./build/labsjdks/release/labsjdk-ce-11.0.18-jvmci-22.3-b13/Contents/Home/bin/java --version      
openjdk 11.0.18 2023-01-17
OpenJDK Runtime Environment (build 11.0.18+10-jvmci-22.3-b13)
OpenJDK 64-Bit Server VM (build 11.0.18+10-jvmci-22.3-b13, mixed mode)
```

iOS static libraries build instructions:
   - build jdk normally for MacOS
   - open jdk-11-ios.xcodeproj in the XCode and press build button or
   - build the jdk-11-ios.xcodeproj project form command line with xcodebuild.sh ...
 
