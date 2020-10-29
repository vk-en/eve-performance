# Results for fio on Ubuntu 20.04 inside VM inside baremetal EVE

## 0.0.0-master-dda8b2b6-kvm

To deploy VM: 

```console
./eden pod deploy --disk-size=6GB --cpus=2 --memory=2GB --metadata="#cloud-config\npassword: passw0rd\nchpasswd: { expire: False }\nssh_pwauth: True\n" -p 8027:22 https://cloud-images.ubuntu.com/releases/focal/release-20200921.1/ubuntu-20.04-server-cloudimg-amd64.img
```

Inside VM:

```
sudo apt-get update
sudo apt-get upgrade -y
wget http://phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_10.0.1_all.deb
sudo apt-get install -y ./phoronix-test-suite_10.0.1_all.deb
phoronix-test-suite run pts/fio
```

Results of pts/fio on Ubuntu 20.04 inside VM inside baremetal EVE:
[openbenchmarking.org](https://openbenchmarking.org/result/2010291-FI-TESTEVE8396)

You can find `iotop  -abtqk |head` output inside [0.0.0-master-dda8b2b6-kvm/iotop](0.0.0-master-dda8b2b6-kvm/iotop)
directory before test, during read test and during write test.