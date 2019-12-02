# Detect an apt-proxy in a Debian environment

## Motivation

Apt caches help to speed up repeated or distributed installations. However, they become problematic when not available.

This package contains an environment to automatically detect if an apt cache is available using the script method and falls back to the direct method if the cache cannot be accessed.

This is especially useful for mobile devices in changing environments.

## Setup

* Copy the file `detect-apt-proxy.sh` to `/usr/local/bin` and  `01proxy` to `/etc/apt/conf.d`

## Shell trail

Install the scripts:
```
sudo mkdir -p /usr/lib/apt-proxy-detect
sudo cp apt-proxy-detect.sh /usr/lib/apt-proxy-detect
sudo cp 01proxy /etc/apt/apt.conf.d/
```
