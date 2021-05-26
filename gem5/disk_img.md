QEMU is a powerful and handy tool to modify a disk image, which gem5 cannot do.
To boot from a given disk image without opening GUI, run this command.

```
qemu-kvm -nographic -enable-kvm -m 1024 -hda <disk-img> -net nic,model=virtio -net user,hostfwd=tcp::2222-:22
```

In this case, the command below should be supplied for access.

```
ssh gem5@localhost -p 2222
```

The above method is handy in that the emulator makes it simple to use common utilities
such as `git`. However, if there is need of moving a file from the host to the disk image,
the method below may be more straightforward.

```
fdisk -l <disk-img> # To get the proper offset
dzdo mount -o loop,offset=1048576 <disk-img> fsmount
# Do whatever to modify the disk
dzdo umount fsmount
```
