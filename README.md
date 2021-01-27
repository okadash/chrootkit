# about

chrootkit is a simple chroot builder and bundler. You can easly create your chroot environment for the specified command set.

```
$ addlib bc some_chrootdir
mkdir: created directory 'some_chrootdir'
mkdir: created directory 'some_chrootdir//lib'
mkdir: created directory 'some_chrootdir//lib/x86_64-linux-gnu'
'/lib/x86_64-linux-gnu/libreadline.so.7' -> 'some_chrootdir//lib/x86_64-linux-gnu/libreadline.so.7'
'/lib/x86_64-linux-gnu/libncurses.so.6' -> 'some_chrootdir//lib/x86_64-linux-gnu/libncurses.so.6'
'/lib/x86_64-linux-gnu/libtinfo.so.6' -> 'some_chrootdir//lib/x86_64-linux-gnu/libtinfo.so.6'
'/lib/x86_64-linux-gnu/libc.so.6' -> 'some_chrootdir//lib/x86_64-linux-gnu/libc.so.6'
'/lib/x86_64-linux-gnu/libdl.so.2' -> 'some_chrootdir//lib/x86_64-linux-gnu/libdl.so.2'
mkdir: created directory 'some_chrootdir//lib64'
'/lib64/ld-linux-x86-64.so.2' -> 'some_chrootdir//lib64/ld-linux-x86-64.so.2'
'/lib/x86_64-linux-gnu/libreadline.so.7' -> 'some_chrootdir//lib/x86_64-linux-gnu/libreadline.so.7'
'/lib/x86_64-linux-gnu/libncurses.so.6' -> 'some_chrootdir//lib/x86_64-linux-gnu/libncurses.so.6'
'/lib/x86_64-linux-gnu/libtinfo.so.6' -> 'some_chrootdir//lib/x86_64-linux-gnu/libtinfo.so.6'
'/lib/x86_64-linux-gnu/libc.so.6' -> 'some_chrootdir//lib/x86_64-linux-gnu/libc.so.6'
'/lib/x86_64-linux-gnu/libdl.so.2' -> 'some_chrootdir//lib/x86_64-linux-gnu/libdl.so.2'
'/lib64/ld-linux-x86-64.so.2' -> 'some_chrootdir//lib64/ld-linux-x86-64.so.2'
mkdir: created directory 'some_chrootdir//usr'
mkdir: created directory 'some_chrootdir//usr/bin'
'/usr/bin/bc' -> 'some_chrootdir//usr/bin/bc'
'/usr/bin/bc' -> 'some_chrootdir//usr/bin/bc'
```

If you already have any contents inside `some_chrootdir`, they may be replaced with new libraries or executables (destructive action). Be sure to use new environment.

You can compose the chroot into a docker image, using `podify` command.

```
$ podify some_chrootdir mybc
Sending build context to Docker daemon  23.36MB
Step 1/3 : FROM scratch
 ---> 
Step 2/3 : ADD . /
 ---> b7bafda59918
Step 3/3 : CMD ["/bin/sh"]
 ---> Running in bfff6a8d64aa
 ---> 1b5ad4d24c88
Successfully built 1b5ad4d24c88
Successfully tagged mybc:latest
```

and run the container:

```
$ docker run -it mybc -u 2021 /usr/bin/bc
bc 1.xx.y
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006, 2008, 2012-2017 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
                                                                                                                                                                                               22^16-1
3011361496339065143295
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
