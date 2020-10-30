# Results for fio on Ubuntu 20.10 inside VM inside baremetal EVE

To deploy VM: 

```console
./eden pod deploy --disk-size=6GB --cpus=2 --memory=2GB --metadata="#cloud-config\npassword: passw0rd\nchpasswd: { expire: False }\nssh_pwauth: True\n" -p 8027:22 https://cloud-images.ubuntu.com/releases/groovy/release-20201022.1/ubuntu-20.10-server-cloudimg-amd64.img
```

Inside EVE:

```console
echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" >> /etc/apk/repositories
apk --update add perf sysstat libelf
sh -c "echo -1 >/proc/sys/kernel/perf_event_paranoid"
sh -c "echo 0 > /proc/sys/kernel/kptr_restrict"
```


Inside VM:

```
sudo apt-get update
sudo apt-get upgrade -y
wget http://phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_10.0.1_all.deb
sudo apt-get install -y ./phoronix-test-suite_10.0.1_all.deb
phoronix-test-suite install pts/fio
sed -i "s/<DynamicRunCount>TRUE<\/DynamicRunCount>/<DynamicRunCount>FALSE<\/DynamicRunCount>/" ~/.phoronix-test-suite/user-config.xml
phoronix-test-suite run pts/fio
```

In EVE ssh sessions:

```console
perf record -F 99 -a -g -o /hostfs/persist/perf
```

```console
sar 10 -o /hostfs/persist/sar
```

## 0.0.0-master-dda8b2b6-kvm

Results of pts/fio on Ubuntu 20.10 inside VM inside baremetal EVE:
[openbenchmarking.org](https://openbenchmarking.org/result/2010303-FI-TESTEVE2048)

You can see [perf](0.0.0-master-dda8b2b6-kvm/perf) and [sar](0.0.0-master-dda8b2b6-kvm/sar) results during tests.

## [expand-limit](https://github.com/itmo-eve/eve/commit/3d09c3990353357351019ef7f653fdf885485419)

Results of pts/fio on Ubuntu 20.10 inside VM inside baremetal EVE:
[openbenchmarking.org](https://openbenchmarking.org/result/2010302-FI-TESTLIMIT87)

You can see [perf](expand-limit/perf) and [sar](expand-limit/sar) results during tests.