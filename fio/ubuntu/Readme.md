# Results for fio on Ubuntu 20.04

Results of pts/fio on Ubuntu 20.04:
[openbenchmarking.org](https://openbenchmarking.org/result/2010308-FI-BARETEST971)

To run benchmark:

```
sudo apt-get update
sudo apt-get upgrade -y
wget http://phoronix-test-suite.com/releases/repo/pts.debian/files/phoronix-test-suite_10.0.1_all.deb
sudo apt-get install -y ./phoronix-test-suite_10.0.1_all.deb
phoronix-test-suite install pts/fio
sed -i "s/<DynamicRunCount>TRUE<\/DynamicRunCount>/<DynamicRunCount>FALSE<\/DynamicRunCount>/" ~/.phoronix-test-suite/user-config.xml
phoronix-test-suite run pts/fio
```

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

You can see [perf](perf) and [sar](sar) results during tests.