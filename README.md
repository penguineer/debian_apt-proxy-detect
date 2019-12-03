# Detect an apt-proxy in a Debian environment

> Detect and use an apt cache if available.

## Motivation

Apt caches help to speed up repeated or distributed installations. However, they become problematic when not available.

This package contains an environment to automatically detect if an apt cache is available using the script method and falls back to the direct method if the cache cannot be accessed.

This is especially useful for mobile devices in changing environments.

## Setup

* Install using CMake (see below)

## Shell trail

Install the scripts using CMake from the source directory:
```
mkdir build
cd build
cmake ..
sudo make install
```

Make a release:
```
mkdir build
cd build
cmake ..
make package
```
