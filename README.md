zstd-android
============

This is a for of [Zstd-jni](https://github.com/luben/zstd-jni) that tries to bring Zstd to android. Simply add this as module to Android Studio and add it as dependency, Android Studio will handle the compilation and packaging for you (Note that it 
requires the NDK and CMake to be installed, for debugging LLDB is needed as well). Below is a copy of the original readme:

Overview
--------

JNI bindings for **Zstd** native library that provides fast and high
compression lossless algorithm for Java and all JVM languages:

* static compress/decompress methods

* implementation of InputStream and OutputStream for transparent compression
of data streams fully compatible with the "zstd" program.

* minimal performance overhead

Zstd
----

**Zstd**, short for Zstandard, is a new lossless compression algorithm, which
provides both good compression ratio _and_ speed for your standard compression
needs. "Standard" translates into everyday situations which neither look for
highest possible ratio (which LZMA and ZPAQ cover) nor extreme speeds (which
LZ4 covers).

**Zstd** is developed by Yann Collet and the source is available at:
https://github.com/facebook/zstd

The motivation for development, the algotithm used and its properties are
explained in the blog post that introduces the library:
http://fastcompression.blogspot.com/2015/01/zstd-stronger-compression-algorithm.html

Status and availability
-----------------------

**Zstd** is production ready with a stable format.

**Zstd-jni** is tracking the release branch of **Zstd** (master) with
compatibility support for the legacy formats (since version 0.4).

**Zstd-jni** version uses the base **Zstd** version with **Zstd-jni** release
appended with a dash, e.g. "1.2.0-2" is the second **Zstd-jni** release based
on **Zstd** version 1.2.0.

Building and dependencies
-------------------------

**Zstd-jni** uses SBT for building the libary and running the tests.

The build system depends on Scala and the tests depend on ScalaTest and
ScalaCheck but the produced JAR does not have any dependencies. It also
embeds the native library.

How to build:

```
 $ sbt compile test package
```

If you want to publish it to you local ivy2 repository:

```
 $ sbt publish-local
```

Binary releases
---------------

The binary releases are architecture dependent because we are embedding the
native library in the provided Jar file. Currently they are built for
*linux-amd64*, *linux-i386*, *linux-aarch64*, *linux-ppc64*,  *win-amd64*,
*win-x86*, *aix-ppc64* and *max_os_x-x86_64*. More builds will be available
if I get access to more platforms.

You can find published releases on Maven Central.

    <dependency>
        <groupId>com.github.luben</groupId>
        <artifactId>zstd-jni</artifactId>
        <version>VERSION</version>
    </dependency>

sbt dependency:

    libraryDependencies += "com.github.luben" % "zstd-jni" % "VERSION"

Link for direct download if you don't use a dependency manager:

 - https://repo1.maven.org/maven2/com/github/luben/zstd-jni/

If there is not yet a binary release compatible with your platform look how
to build it locally under the [Building](#building-and-dependencies) section.

License
-------

The code for these JNI bindings is licenced under 2-clause BSD license.
The native **Zstd** library is licensed under 3-clause BSD license and
GPL2. See the LICENSE file and LICENSE and COPYRIGHT in src/main/native
for full copyright and conditions.
