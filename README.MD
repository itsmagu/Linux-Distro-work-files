## This is mostly stable, but not production ready in any way.
Exiting the shell will kernel panic for instance
# Building
```./buildInitramfs && ./buildCpio && ./buildKernel && ./copyToBootFile && ./pushToVM```
# Running
I run with Qemu on a Windows host

### Arguments:
```qemu-system-x86_64.exe C:\VM\boot -nographic -serial mon:stdio -m 1G```
