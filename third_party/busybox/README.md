BusyBox (GPLv2)

This directory contains BusyBox version 1.36.1.

Source:
https://busybox.net/downloads/

License:
GNU General Public License v2.0 only

---

**Modifications:**  
This build includes local modifications to the upstream BusyBox source.

The exact upstream BusyBox source tarball is included unmodified. All changes are applied via a unified diff patch (static_zig.patch) during build.

---

**Build configuration:**   
The BusyBox configuration used for this build is stored in:
    busybox.config

---

**Toolchain:**  
This project is built using Zig for cross-compilation:  
    `zig cc -target aarch64-linux-musl`

Ensure Zig is installed on the host system.

---

**Build instructions:**  

``` 
tar -xvjf busybox-1.36.1.tar.bz2

patch -p1 -d busybox-1.36.1/ < static_zig.patch

cp busybox.config busybox-1.36.1/.config

cd busybox-1.36.1

make oldconfig

make -j$(nproc) \
    CC="zig cc -target aarch64-linux-musl -O2 -static" \
    SKIP_STRIP=y \
    CONFIG_PREFIX=../rootfs \
    install
```