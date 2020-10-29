# Results for fio on Ubuntu 20.04

Results of pts/fio on Ubuntu 20.04:
[openbenchmarking.org](https://openbenchmarking.org/result/2010299-FI-TESTBARE692)

You can find `iotop  -abtqk |head` output inside [iotop](iotop) directory [before](iotop/before.txt) test,
during [read](iotop/read.txt) test and during [write](iotop/write.txt) test.

To run benchmark:

```
sudo apt-get update
sudo apt-get upgrade -y
wget http://phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_10.0.1_all.deb
sudo apt-get install -y ./phoronix-test-suite_10.0.1_all.deb
phoronix-test-suite run pts/fio
```