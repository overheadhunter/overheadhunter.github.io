---
layout: post
title:  "Building JNI-Libraries on Windows with MinGW-w64"
date:   2016-09-03
tags: [java, open source, jni, windows, c++]
---
I needed to build a JNI lib for Windows, both 64 and 32 bit. However I didn't want to install that 5 GiB monster called Visual Studio just to build a small .cpp file. The open source gcc port MinGW seems to be the better alternative.

### Setup compiler
Decide on a MinGW toolchain distribution, described [on wiki.qt.io](https://wiki.qt.io/MinGW-64-bit).
My choices:
- mingw-builds
- version 6.2.0
- threads-win32
- SEH

Downloaded from [SourceForge](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/6.2.0/threads-win32/seh/) and extracted the contained folder to `C:\mingw64`. Once done, I added `C:\mingw64\bin` to the `PATH` variable.

### Single Sign-On protocols aren't designed for this
At first glance this isn't a new problem, there are tons of solutions out there: Just do a quick google search on "single sign on". The only problem is, that SSO systems are designed to prove the user's authenticity to a third party service by confirming his or her identity. But in our case the exact opposite is needed: We need to prove legitimacy without leaking the user's identity.
