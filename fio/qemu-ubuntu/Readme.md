# Results for fio on Ubuntu 20.10 VM inside Ubuntu 20.04 host

Results of pts/fio on Ubuntu 20.04 inside VM on Ubuntu 20.04 host:
[openbenchmarking.org](https://openbenchmarking.org/result/2010305-FI-TESTUBQEM48)

VM was started with provided [config](qemu.conf) by command
`qemu-system-x86_64 -nographic -display none -serial telnet:localhost:7777,server,nowait -nodefaults -overcommit cpu-pm=on -no-hpet -no-user-config -readconfig /home/giggsoff/local/qemu.conf`
with [image](https://cloud-images.ubuntu.com/releases/groovy/release-20201022.1/ubuntu-20.10-server-cloudimg-amd64.img)
moved into `ubuntu.qcow2` and expanded by `qemu-img resize ubuntu.qcow2 6G` and.
Also, you need to generate cloud-init iso.

Inside Host system:

```console
sudo sh -c "echo -1 >/proc/sys/kernel/perf_event_paranoid"
sudo sh -c "echo 0 > /proc/sys/kernel/kptr_restrict"
```

```console
perf record -F 99 -a -g -o /hostfs/persist/perf
```

```console
sar 10 -o /hostfs/persist/sar
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

You can see [perf](perf) and [sar](sar) results during tests.