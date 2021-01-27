# about

chrootkit is a simple chroot builder and bundler. You can easly create your chroot environment for the specified command set.

```
addlib bc some_chrootdir
```

If you already have any contents inside `some_chrootdir`, they may be replaced with new libraries or executables (destructive action). Be sure to use new environment.

You can compose the chroot into docker images, using `podify` command.

```
podify some_chrootdir mybc
```

# Requirement

* a shell with posix compliant behaivior (busybox, bash, dash, etc.)
* GNU AWK
* docker (if you need to pack them inside a docker image)
* POSIX compliant readlinkf (recommended)

# Usage

addlib [</path/to/executable>, ...] \<destination\>

podify \<root\> [name]

# Author

okadas[at]tanban.org
