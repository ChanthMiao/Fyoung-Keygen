# Fyoung-Keygen
A keygen of China Telecom Fyoung Dialer.

I only tested this program in SCU. Maybe it's same to other colleges in Chengdu. 

## Sketch

Decompile from v2.23 macOS dialer(single dialing).

The keygen can generate the true username of PPPoE dial.

**Notice: This keygen doesn't handle the heartbeat packets, so the connection may be aborted every 24 hours more or less.**

&copy; 2018 xiaopc, all rights reserved & profitable use forbidden. 

**Legal notice: you should realize that ALL THE CONSEQUENCES, INCLUDING LEGAL LIABILITY, WERE ON YOUR OWN IF YOU USE THIS PROGRAM!**

## Compile

The keygen is designed for routers, you may want to use specific toolchain, e.g. mipsel-openwrt-linux-uclibc-gcc.

```bash
gcc -c MD5.c -std=c99
gcc -c fyoung.c -std=c99
gcc -o fyoung fyoung.o MD5.o
```

## Usage

In router's `ppp.sh` (mine locates at `/lib/netifd/proto/`) , after where username & password's variables are generated , e.g.:

```bash
json_get_vars ipv6 demand keepalive keepalive_adaptive username password pppd_options pppname unnumbered
```

Add:

```
username=$(/usr/sbin/fyoung $username $password)
```

When dialing, add `tyfy` before your username(if not, it will return original username).
