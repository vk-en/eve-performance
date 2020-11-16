
# Results for FIO on Ubuntu 20.10 VM inside EVE 

Testing was run by the FIO utility on a virtual machine created in EVE. The tests took into account the utilization of the disk on which the load was running both on the virtual machine in EVE and on EVE itself.

---

### Results on VM(on EVE) with EXT-4 filesystem 

 FIO pattern | SEQUENTIAL READ | SEQUENTIAL WRITE | SEQUENTIAL READ without fs
----------------------------------- | -------------------------- | -------------------------- | --------------------------
bs=4k direct=1 numjobs=1 iodepth=16 | 21.9MB/s, disk util=98.66% | 9377kB/s, disk util=96.75% | 21.9MB/s, disk util=98.66%
bs=4k direct=1 numjobs=8 iodepth=16 | 59.8MB/s, disk util=94.31% | 73.8MB/s, disk util=98.54% | 59.8MB/s, disk util=94.31%
bs=4k direct=1 numjobs=8 iodepth=32 | 74.3MB/s, disk util=94.13% | 85.4MB/s, disk util=95.47% | 74.3MB/s, disk util=94.13%
bs=4k direct=1 numjobs=1 iodepth=32 | 31.8MB/s, disk util=98.55% | 13.3MB/s, disk util=96.89% | 31.8MB/s, disk util=98.55%
bs=64k direct=1 numjobs=1 iodepth=16 | 1078MB/s, disk util=98.68% | 13.4MB/s, disk util=88.20% | 167MB/s, disk util=99.05%
bs=64k direct=1 numjobs=8 iodepth=16 | 1077MB/s, disk util=91.65% | 108MB/s,  disk util=95.24% | 154MB/s, disk util=95.82%
bs=64k direct=1 numjobs=8 iodepth=32 | 1159MB/s, disk util=90.83% | 95.8MB/s, disk util=90.99% | 150MB/s, disk util=95.74%
bs=64k direct=1 numjobs=1 iodepth=32 | 1472MB/s, disk util=97.87% | 13.5MB/s, disk util=99.14% | 147MB/s, disk util=99.16%
bs=1m direct=1 numjobs=1 iodepth=16 | 1978MB/s, disk util=99.67% | 13.2MB/s, disk util=93.42% | 188MB/s, disk util=99.84%
bs=1m direct=1 numjobs=8 iodepth=16 | 2324MB/s, disk util=88.42% | 99.7MB/s, disk util=98.01% | 182MB/s, disk util=99.52%
bs=1m direct=1 numjobs=8 iodepth=32 | 2612MB/s, disk util=93.28% | 36.8MB/s, disk util=98.38% | 175MB/s, disk util=99.63%
bs=1m direct=1 numjobs=1 iodepth=32 | 2036MB/s, disk util=97.81% | 13.6MB/s, disk util=97.57% | 188MB/s, disk util=99.44%

We also monitored disk utilization on EVE itself through the **iostat** utility.

> Most of the sequential write results may not reflect the actual results in terms of speed and utilization, because the disk utilization for writing according to iostat was in the range of 99% to 250%. In this regard, there were failures in FIO, which influenced the final result of both speed and utilization. Disk utilization both on the VM and on EVE itself was the maximum in all write tests.

> Disk utilization on VM during reading tests was also 90%. But on EVE, disk utilization only rarely reached 99%. The average value of disk utilization on EVE during reading tests on VM was in the average range from 30% to 60% based on observations of statistics on iostat (with an interval of 3 seconds). 

---

### Results on VM(on EVE) with XFS filesystem 


 FIO pattern | SEQUENTIAL READ | SEQUENTIAL WRITE | SEQUENTIAL READ without fs
----------------------------------- | -------------------------- | -------------------------- | --------------------------
`bs=4k direct=1 numjobs=1 iodepth=16` | | | 
`bs=4k direct=1 numjobs=8 iodepth=16` | | | 
`bs=4k direct=1 numjobs=8 iodepth=32` | | | 
`bs=4k direct=1 numjobs=1 iodepth=32` | | | 
`bs=64k direct=1 numjobs=1 iodepth=16` | | |
`bs=64k direct=1 numjobs=8 iodepth=16` | | |
`bs=64k direct=1 numjobs=8 iodepth=32` | | |
`bs=64k direct=1 numjobs=1 iodepth=32` | | |
`bs=1m direct=1 numjobs=1 iodepth=16` | | | 
`bs=1m direct=1 numjobs=8 iodepth=16` | | | 
`bs=1m direct=1 numjobs=8 iodepth=32` | | | 
`bs=1m direct=1 numjobs=1 iodepth=32` | | | 

