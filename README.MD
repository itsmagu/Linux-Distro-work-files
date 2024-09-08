A Simple collection of scripts to build a super small "distro" that only runs the kernel as a starting point

This is stable, but not production ready in any way. <br>
Exiting the shell will kernel panic.
The build process is not really that portable either and will litter(mess with files outside of build dir) a system on building.
And I'm aware that the "project" structure is messy, But... it boots! This was hobby thing mostly.

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
In Bootstrap System (ArchWSL): <br>
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
arch-install-scripts base base-devel bat bc bison bottom clang cmake cpio devtools dosfstools elfutils fakeroot-tcp fd fish flex gcc gdb htop man-db mesa mesa-utils mtools nano neofetch neovim ninja nodejs nvtop ranger ripgrep sdl2 sudo syslinux tmux unzip vim wget xf86-video-vesa zig
```
All packages for void (whole install command):
```
xbps-install base-devel bat bc bison bottom clang cmake cpio git curl wget unzip binutils diffutils grep ripgrep jq openssh rsync dosfstools elfutils fd fish-shell flex lz4 htop man-db mesa mesa-dri mesa-intel-dri mesa-nouveau-dri elfutils-devel mesa-opencl mesa-vulkan-intel mtools neovim ninja nodejs nvtop ncurses-devel ranger SDL2 SDL2-devel syslinux tmux xf86-video-fbdev xf86-video-vesa xf86-ideo-nouveau xf86-video-intel zig rustup
```
or:
```
SDL2-2.28.5_3
SDL2-devel-2.28.5_3
base-devel-20181003_2
base-voidstrap-0.11_2
bat-0.24.0_1
bc-1.07.1_5
binutils-2.41_1
bison-3.8.2_1
bottom-0.9.6_1
clang-17_2
cmake-3.27.6_1
cpio-2.15_1
curl-8.6.0_1
elfutils-0.190_1
elfutils-devel-0.190_1
fd-9.0.0_2
fish-shell-3.7.0_1
flex-2.6.4_3
git-2.43.2_1
htop-3.3.0_1
jq-1.7.1_1
lz4-1.9.4_1
man-db-2.11.2_1
mesa-23.3.5_3
mesa-dri-23.3.5_3
mesa-intel-dri-23.3.5_3
mesa-nouveau-dri-23.3.5_3
mesa-opencl-23.3.5_3
mesa-vulkan-intel-23.3.5_3
mtools-4.0.43_1
ncurses-devel-6.4_2
neovim-0.9.5_1
ninja-1.11.1_4
nodejs-18.19.1_1
nvtop-3.0.2_1
ranger-1.9.3_5
ripgrep-14.1.0_1
rsync-3.2.7_2
rustup-1.26.0_2
syslinux-6.03_8
tmux-3.4_1
unzip-6.0_15
wget-1.21.4_2
xf86-video-fbdev-0.5.0_2
xf86-video-intel-2.99.917.20210115_2
xf86-video-nouveau-1.0.17_2
xf86-video-vesa-2.6.0_1
zig-0.10.1_3
```
