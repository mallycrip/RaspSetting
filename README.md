### Set
```bash
$ chmod +777 ${shellFile}.sh
```

### Change docker daemon driver
```bash
$ sudo cat > /etc/docker/daemon.json <<EOF
{
  "exec-opts": ["native.cgroupdriver=systemd"],
  "log-driver": "json-file",
  "log-opts": {
    "max-size": "100m"
  },
  "storage-driver": "overlay2"
}
EOF
$ sudo mkdir -p /etc/systemd/system/docker.service.d
$ sudo systemctl daemon-reload
$ sudo systemctl restart docker
```
### Ref
- https://ubuntu.com/tutorials/how-to-kubernetes-cluster-on-raspberry-pi#1-overview