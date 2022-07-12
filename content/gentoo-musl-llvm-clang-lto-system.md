+++
title = "clang llvm lto musl gentoo system"
date = 2022-07-12
description = "clang llvm lto musl gentoo system"
+++

# Steps

- firstly get started with the minimal installation cd
- follow all the steps until downloading the stage3 where you install the stage 3 musl not glibc musl. 
***If you are wondering what is musl***

- for the use flags the important ones being clang and lto

also the local use flag to enable for clang would be default-lld

sample make.conf

```conf
# Normal settings here
COMMON_FLAGS="-O2 -march=native"
#COMMON_FLAGS="-march=haswell -O2 -pipe"
CFLAGS="${COMMON_FLAGS} -flto=thin"
CXXFLAGS="${COMMON_FLAGS} -flto=thin"
LDFLAGS="${LDFLAGS} -Wl,-O2 -Wl,--as-needed"

CC="clang"
CXX="clang++"
AR="llvm-ar"
NM="llvm-nm"
RANLIB="llvm-ranlib"

LDFLAGS="${LDFLAGS} -fuse-ld=lld -rtlib=compiler-rt -unwindlib=libunwind -Wl,--as-needed"

# Hardening which isn't (yet?) done by default for Clang, unlike GCC.
_HARDENING_FLAGS="-fstack-protector-strong -D_FORTIFY_SOURCE=2"
CFLAGS="${CFLAGS} ${_HARDENING_FLAGS}"
CXXFLAGS="${CXXFLAGS} ${_HARDENING_FLAGS}"
LDFLAGS="${LDFLAGS} -Wl,-z,relro,-z,now"

#and etc.
ACCEPT_LICENSE="*"
USE="-kde -systemd -gnome -cdinstall -cdr -css -iee1394 -emboss -3dfx -altivec -ibm -cups -dvd -dvdr -a52 alsa X xinerama python pulseaudio networkmanager bluetooth ***clang lto***"
QEMU_SOFTMMU_TARGETS="*"
QEMU_USER_TARGETS="*"
LC_MESSAGES=C
```
also follow the guide make a gcc fallback env and clang-no-lto


musl is another standard c library that clang can compile while musl can not
- while you are at it install clang in the method explained in the wiki.
- while doing the clang/llvm genkernel use the options --kernel-cc to compile it with clang/llvm (look into gentoo wiki on clang for more info)
