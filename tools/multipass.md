[`multipass`](https://multipass.run/?_ga=2.49373798.1927342598.1634912166-336090803.1634912166) is recommended by the Ubuntu website.

It is extremely hard to locate the disk image used by `multipass`. It turns out to sit in the directory included in the command below.
Besides that, it has been a pleasing experience using this tool.

Use this command to resize the disk image on macOS.

```
VBoxManage modifyhd --resize 15000 /var/root/Library/Application\ Support/multipassd/virtualbox/vault/instances/ubuntu-lts-multipass/ubuntu-20.04-server-cloudimg-amd64.vdi
```
