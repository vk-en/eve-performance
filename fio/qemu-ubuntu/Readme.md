# Results for fio on Ubuntu 20.04 VM inside Ubuntu 20.04 host

Results of pts/fio on Ubuntu 20.04 inside VM on Ubuntu 20.04 host:
[openbenchmarking.org](https://openbenchmarking.org/result/2010293-FI-TESTUBUNT76)

You can find `iotop  -abtqk |head` output inside [iotop](iotop) directory [before](iotop/before.txt) test,
during [read](iotop/read.txt) test and during [write](iotop/write.txt) test.

VM was started with provided [config](qemu.conf)
with [image](https://cloud-images.ubuntu.com/releases/focal/release-20200921.1/ubuntu-20.04-server-cloudimg-amd64.img).

Inside VM:

```
sudo apt-get update
sudo apt-get upgrade -y
wget http://phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_10.0.1_all.deb
sudo apt-get install -y ./phoronix-test-suite_10.0.1_all.deb
phoronix-test-suite run pts/fio
```