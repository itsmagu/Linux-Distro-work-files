This is stable, but not production ready in any way. <br>
Exiting the shell will kernel panic for instance.
This is not really that portable either and will litter(mess with files outside of build dir) a system on building.
And yes, they files are dirty and does alot of BM without a standard or reason. But... it boots!

![](docs/img/linuxinashell.gif)
# Not Linux From Scratch
This is a fun hobby project where I have made some scripts for quick and easy creation and booting
of a linux kernel and inital file system. It's super small and fast, infact the gif right above
competes with both file size and time to complete/boot! No, but seriously it's super fast and small.
Beware though, there is not init system (systemd/openRC/runit). No real folder structure (like /proc /var).
But it is amazing at running only one thing and could be used as a base for a new distro or a gaming console if
you throw in some SDL2 in it. As of writing this, I have no real plan other then exploring how this all works 
under the hood. I'll strip the kernel some more and maybe move this into a raspberry pi console... <br>

# Building
In Bootstarp System (ArchWSL): <br>
```git clone https://github.com/itsmagu/Not-LFS /work-files/```
In order: <br>
```
sh ./initalize
./fetchSources # Make sure that Busybox compiles as static (make menuconfig)
./buildKernel
./buildInitramfs
./buildCpio
./copyToBootFile
./pushToVM
```
TODO: move to make (I am just lazy, but lot of files are messy) <br>

# Running
I run with Qemu on a Windows host: <br>
```qemu-system-x86_64.exe C:\VM\boot -nographic -serial mon:stdio -m 1G```

## Prerequisites
I use ArchLinux as the bootstrap system in WSL on windows (Google the repo for ArchWSL)<br>
The Scripts expect a "C:/VM/" dir on the host windows system for qemu to boot
and a "root/source" in the WSL system. If you understand how this all works you can
edit and change the folders or even from ArchWSL and the Windows host setup. <br>

All Packages from my system (Even useless ones)(That is not included in ArchWSL by normal):
```
arch-install-scripts
base
base-devel
bat
bc
bison
bottom
clang
cmake
cpio
devtools
dosfstools
elfutils
fakeroot-tcp
fd
fish
flex
gcc
gdb
htop
man-db
mesa
mesa-utils
mtools
nano
neofetch
neovim
ninja
nodejs
nvtop
ranger
ripgrep
sdl2
sudo
syslinux
tmux
unzip
vim
wget
xf86-video-vesa
zig
```
