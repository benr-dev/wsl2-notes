# WSL2 Notes

## Network Config

By default, WSL2 will configure /etc/hosts and /etc/resolv.conf itself which breaks local DNS resolution.

To avoid this, perform the following configuration after sign-in:

- Stop WSL configuring the networking itself
```
sudo /etc/wsl.conf

[network]
generateHosts = false
generateResolvConf = false
```

- Configure the DNS
```
sudo /etc/resolv.conf

nameserver X.X.X.X
nameserver Y.Y.Y.Y
```

- Add any additional static servers to hosts
```
sudo /etc/hosts

Z.Z.Z.Z  some-other-server
...
```

- Shutdown the VM
```
(in a windows terminal)

wsl --terminate Debian
```

Restart the WSL terminal and DNS should work as expected