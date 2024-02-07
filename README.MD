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
arch-install-scripts 28-1
base 3-2
base-devel 1-1
bat 0.24.0-1
bc 1.07.1-4
bison 3.8.2-6
bottom 0.9.6-1
clang 16.0.6-2
cmake 3.28.2-1
cpio 2.15-1
devtools 1:1.0.4-1
dosfstools 4.2-3
elfutils 0.190-1
fakeroot-tcp 1.25.3-2
fd 9.0.0-1
fish 3.7.0-1
flex 2.6.4-5
gcc 13.2.1-4
gdb 14.1-1
htop 3.3.0-1
man-db 2.12.0-1
mesa 1:23.3.5-1
mesa-utils 9.0.0-3
mtools 1:4.0.43-1
nano 7.2-1
neofetch 7.1.0-2
neovim 0.9.5-2
ninja 1.11.1-3
nodejs 21.6.1-1
nvtop 3.0.2-1
ranger 1.9.3-9
ripgrep 14.1.0-1
sdl2 2.28.5-1
sdl2_gfx 1:1.0.4-3
sdl2_image 2.8.2-2
sdl2_mixer 2.8.0-1
sdl2_net 1:2.2.0-1
sdl2_ttf 2.22.0-1
sudo 1.9.15.p5-1
syslinux 6.04.pre2.r11.gbf6db5b4-4
tmux 3.3_a-7
unzip 6.0-20
vim 9.1.0000-1
wget 1.21.4-1
xf86-video-intel 1:2.99.917+923+gb74b67f0-1
xf86-video-nouveau 1.0.17-2
xf86-video-vesa 2.6.0-1
xorg-server 21.1.11-1
xorg-xcalc 1.1.2-1
zig 0.11.0-1
```
