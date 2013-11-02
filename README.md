sfntly-builds
=============

Builds of sfntly from https://code.google.com/p/sfntly/

Instructions are a bit sparse over there, especially with regards to dependancies needed to build it.

Java
------

#### On Ubuntu 13.10 (or others with openjdk-7 by default)
```bash
apt-get install openjdk-7-jdk
```

#### On older versions (Ubuntu 12.04 LTS for example), you need to use either openjdk-6 or openjdk-7

update-alternatives should tidy up the multiple versions so it works. Chances are you don't really need both versions installed simultaneously!

##### To force/use 
```bash
apt-get purge openjdk-6-jre-lib openjdk-6-jre-headless
apt-get install openjdk-7-jdk
```

##### To force/use 6
```bash
apt-get purge openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib
apt-get install openjdk-6-jdk
```

#### Then for all versions
```bash
apt-get install subversion ant
svn checkout http://sfntly.googlecode.com/svn/trunk/ sfntly-read-only
cd sfntly-read-only/java/
ant
```

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
