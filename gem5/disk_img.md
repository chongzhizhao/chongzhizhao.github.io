QEMU is a powerful and handy tool to modify a disk image, which gem5 cannot do.
To boot from a given disk image without opening GUI, run this command.

```
qemu-kvm -nographic -enable-kvm -m 1024 -hda proj-disk-img -net nic,model=virtio -net user,hostfwd=tcp::2222-:22
```

In this case, the command below should be supplied for access.

```
ssh gem5@localhost -p 2222
```
