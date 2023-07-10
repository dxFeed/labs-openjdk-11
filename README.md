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
1. Clone this repo and checkout to branch `release/jvmci/22.3-b13-fix-sun-management`
2. Add oracle origin: `https://github.com/graalvm/labs-openjdk-11.git`

```
$ git remote add oracle https://github.com/graalvm/labs-openjdk-11.git
$ git fetch oracle               
remote: Enumerating objects: 4743, done.
remote: Counting objects: 100% (4677/4677), done.
remote: Compressing objects: 100% (2042/2042), done.
remote: Total 4743 (delta 2414), reused 4667 (delta 2408), pack-reused 66
Receiving objects: 100% (4743/4743), 7.78 MiB | 10.69 MiB/s, done.
Resolving deltas: 100% (2415/2415), completed with 52 local objects.
From https://github.com/graalvm/labs-openjdk-11
 * [new branch]            master             -> oracle/master
 * [new branch]            release/jvmci/19.3 -> oracle/release/jvmci/19.3
 * [new branch]            release/jvmci/20.0 -> oracle/release/jvmci/20.0
 * [new branch]            release/jvmci/20.1 -> oracle/release/jvmci/20.1
 * [new branch]            release/jvmci/20.3 -> oracle/release/jvmci/20.3
 * [new branch]            release/jvmci/21.0 -> oracle/release/jvmci/21.0
 * [new branch]            release/jvmci/21.1 -> oracle/release/jvmci/21.1
 * [new branch]            release/jvmci/21.2 -> oracle/release/jvmci/21.2
 * [new branch]            release/jvmci/21.3 -> oracle/release/jvmci/21.3
 * [new branch]            release/jvmci/22.0 -> oracle/release/jvmci/22.0
 * [new branch]            release/jvmci/22.1 -> oracle/release/jvmci/22.1
 * [new branch]            release/jvmci/22.2 -> oracle/release/jvmci/22.2
 * [new branch]            release/jvmci/22.3 -> oracle/release/jvmci/22.3
 * [new tag]               jdk-11.0.16.1+0    -> jdk-11.0.16.1+0
 * [new tag]               jdk-11.0.16.1+1    -> jdk-11.0.16.1+1
 * [new tag]               jdk-11.0.16.1-ga   -> jdk-11.0.16.1-ga
 * [new tag]               jdk-11.0.17+0      -> jdk-11.0.17+0
 * [new tag]               jdk-11.0.17+1      -> jdk-11.0.17+1
 * [new tag]               jdk-11.0.17+2      -> jdk-11.0.17+2
 * [new tag]               jdk-11.0.17+3      -> jdk-11.0.17+3
 * [new tag]               jdk-11.0.17+4      -> jdk-11.0.17+4
 * [new tag]               jdk-11.0.17+5      -> jdk-11.0.17+5
 * [new tag]               jdk-11.0.17+6      -> jdk-11.0.17+6
 * [new tag]               jdk-11.0.17+7      -> jdk-11.0.17+7
 * [new tag]               jdk-11.0.17+8      -> jdk-11.0.17+8
 * [new tag]               jdk-11.0.17-ga     -> jdk-11.0.17-ga
 * [new tag]               jdk-11.0.18+0      -> jdk-11.0.18+0
 * [new tag]               jdk-11.0.18+1      -> jdk-11.0.18+1
 * [new tag]               jdk-11.0.18+10     -> jdk-11.0.18+10
 * [new tag]               jdk-11.0.18+2      -> jdk-11.0.18+2
 * [new tag]               jdk-11.0.18+3      -> jdk-11.0.18+3
 * [new tag]               jdk-11.0.18+4      -> jdk-11.0.18+4
 * [new tag]               jdk-11.0.18+5      -> jdk-11.0.18+5
 * [new tag]               jdk-11.0.18+6      -> jdk-11.0.18+6
 * [new tag]               jdk-11.0.18+7      -> jdk-11.0.18+7
 * [new tag]               jdk-11.0.18+8      -> jdk-11.0.18+8
 * [new tag]               jdk-11.0.18+9      -> jdk-11.0.18+9
 * [new tag]               jdk-11.0.18-ga     -> jdk-11.0.18-ga
 * [new tag]               jdk-11.0.19+0      -> jdk-11.0.19+0
 * [new tag]               jvmci-22.3-b04     -> jvmci-22.3-b04
 * [new tag]               jvmci-22.3-b05     -> jvmci-22.3-b05
 * [new tag]               jvmci-22.3-b06     -> jvmci-22.3-b06
 * [new tag]               jvmci-22.3-b07     -> jvmci-22.3-b07
 * [new tag]               jvmci-22.3-b08     -> jvmci-22.3-b08
 * [new tag]               jvmci-22.3-b09     -> jvmci-22.3-b09
 * [new tag]               jvmci-22.3-b10     -> jvmci-22.3-b10
 * [new tag]               jvmci-22.3-b12     -> jvmci-22.3-b12
 * [new tag]               jvmci-22.3-b13     -> jvmci-22.3-b13
 * [new tag]               jdk-11.0.19+1      -> jdk-11.0.19+1
 * [new tag]               jdk-11.0.19+2      -> jdk-11.0.19+2
 * [new tag]               jdk-11.0.19+3      -> jdk-11.0.19+3
 * [new tag]               jdk-11.0.19+4      -> jdk-11.0.19+4
 * [new tag]               jdk-11.0.19+5      -> jdk-11.0.19+5
 * [new tag]               jdk-11.0.19+6      -> jdk-11.0.19+6
 * [new tag]               jdk-11.0.19+7      -> jdk-11.0.19+7
 * [new tag]               jdk-11.0.19-ga     -> jdk-11.0.19-ga
 * [new tag]               jdk-11.0.20+0      -> jdk-11.0.20+0
 * [new tag]               jdk-11.0.20+1      -> jdk-11.0.20+1
 * [new tag]               jdk-11.0.20+2      -> jdk-11.0.20+2
 * [new tag]               jdk-11.0.20+3      -> jdk-11.0.20+3
 * [new tag]               jdk-11.0.20+4      -> jdk-11.0.20+4
 * [new tag]               jdk-11.0.20+5      -> jdk-11.0.20+5
 * [new tag]               jdk-11.0.20+6      -> jdk-11.0.20+6
 * [new tag]               jdk-11.0.20+7      -> jdk-11.0.20+7
 * [new tag]               jdk-11.0.21+7      -> jdk-11.0.21+7
 * [new tag]               jvmci-21.3-b23     -> jvmci-21.3-b23
 * [new tag]               jvmci-22.3-b14     -> jvmci-22.3-b14
 * [new tag]               jvmci-22.3-b16     -> jvmci-22.3-b16
 * [new tag]               jvmci-22.3-b17     -> jvmci-22.3-b17
 * [new tag]               jvmci-22.3-b18     -> jvmci-22.3-b18
 * [new tag]               jvmci-23.0-b01     -> jvmci-23.0-b01
```

2. Download https://github.com/graalvm/labs-openjdk-11/releases/tag/jvmci-22.3-b13

3. Remove `com.apple.quarantine` from downloaded ZIP and unpack it
```
$ xattr -d com.apple.quarantine ./labsjdk-ce-11.0.18+10-jvmci-22.3-b13-darwin-amd64.tar.gz
$ Unpack ZIP to labsjdk-ce-11.0.18-jvmci-22.3-b13
$ export JAVA_HOME=<ABSOLUTE_PATH>/labsjdk-ce-11.0.18-jvmci-22.3-b13/Contents/Home
```

4. Verify downloaded build version
```
$ java --version                                                                                   
openjdk 11.0.18 2023-01-17
OpenJDK Runtime Environment (build 11.0.18+10-jvmci-22.3-b13)
OpenJDK 64-Bit Server VM (build 11.0.18+10-jvmci-22.3-b13, mixed mode)

```
5. Go to the cloned repo directory and build `JVMCI_VERSION=22.3-b13`
```
cd labs-openjdk-11
python3 build_labsjdk.py --jvmci-version 22.3-b13 --configure-option=--disable-warnings-as-errors
```

iOS static libraries build instructions:
   - build jdk normally for MacOS
   - open jdk-11-ios.xcodeproj in the XCode and press build button or
   - build the jdk-11-ios.xcodeproj project from command line with xcodebuild.sh ...
