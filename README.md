sfntly-builds
=============

Builds of sfntly from https://code.google.com/p/sfntly/

Instructions are a bit sparse over there, especially with regards to dependancies needed to build it.

Java
------

On Ubuntu 14.10 and above, you can install openjdk-8-jdk. On Ubuntu 13.10 and above, you can install openjdk-7-jdk. On older versions (Ubuntu 12.04 LTS for example), you can use either openjdk-6-jdk or openjdk-7-jdk.

#### Swapping between versions

update-alternatives should tidy up the multiple versions so it works. Chances are you don't really need more than one version installed simultaneously anyway!

```bash
update-alternatives --config java
update-alternatives --config javac
```

For each of the above commands you'll get something like the below. Selecting 1/2 as appropriate will allow you to change the "active" openjdk version

```bash
root@ubuntu64-web-esxi:/home/reedy/sfntly-builds# update-alternatives --config javac
There are 2 choices for the alternative javac (providing /usr/bin/javac).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-7-openjdk-amd64/bin/javac   1071      auto mode
* 1            /usr/lib/jvm/java-6-openjdk-amd64/bin/javac   1061      manual mode
  2            /usr/lib/jvm/java-7-openjdk-amd64/bin/javac   1071      manual mode

Press enter to keep the current choice[*], or type selection number:
```

##### To use openjdk-7
```bash
apt-get install openjdk-7-jdk
```

##### To use openjdk-6
```bash
apt-get install openjdk-6-jdk
```

##### To use openjdk-8
```bash
apt-get install openjdk-8-jdk
```

#### Then for all versions
```bash
apt-get install subversion ant
svn checkout http://sfntly.googlecode.com/svn/trunk/ sfntly-read-only
cd sfntly-read-only/java/
ant
```

All built files are then in the dist folder, with the jars in the tools subdir probably being what you want.

sfnttool.jar is at dist/tools/sfnttool/sfnttool.jar

CPP
------
Googles instructions are here: https://code.google.com/p/sfntly/wiki/build_cpp

#### Dependancies
```bash
apt-get install libicu-dev make cmake build-essential unzip
```

#### Commands
```bash
cd cpp/ext/redist
unzip gtest-1.6.0.zip
mv gtest-1.6.0 ../gtest
cd ../..
mkdir build
cd build
cmake ..
make
```

All the executables are then in the bin folder.
