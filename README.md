# aeon-amd-solominer (forked from wolf-xmr-miner)

LesPristy's OpenCL AEON Miner for AMD GPUs

If you get an error about `clCreateBuffer`, lower your `rawintensity`. See the example config [xmr.conf](xmr.conf) for details.

Generally, you want to raise `rawintensity` as high as it will go without error - but remember, 2MiB of GPU RAM is needed for every work-item.

The GPU fan, powertune, and clock setting options are accepted, as the configuration routine was ripped from my own full-custom miner, but they do nothing.

# hyc's additions (Linux only)

Use a GPU index of `-1` to run on the CPU. The only other config item needed is "threads",
but `rawintensity` and `worksize` must still be set to a non-zero value.

As with the original CPU miner, you can gain a performance boost by configuring huge pages.
Check current setting with `sysctl vm.nr_hugepages` then set it to at least 3 times the
total number of threads you're using, as root.

    sudo sysctl -w vm.nr_hugepages=num

Also, it can run faster as root, which allows it to use mlock.

# Solo mining

Use a URL of "daemon+tcp://<host>:<port>" - requires aeond with open RPC port and "blockhashing blob" support.
Stratum pool mining is not supported in this fork.

# Building

## Ubuntu 14.04 or later

Clone the "update" branch.
```
git clone https://github.com/LesPristy/aeon-amd-solominer.git -b update
```

### Installing dependencies

gcc 5 or newer is required.
```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test -y && \
sudo apt-get update && \
sudo apt-get install gcc-6 g++-6 libjansson-dev -y && \
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-6 60 --slave /usr/bin/g++ g++ /usr/bin/g++-6
```

### Building and running

```
make
./miner aeon.conf
```
You can mine using my public node, or you can set up your own node. You must have a version of aeond with Monero "blockhashing blob" support.

There is no devfee. Be sure to update aeon.conf with your own AEON address, unless you feel like mining to my address!

# Donations
LesPristy donation address
* AEON: `WmtDvD5V3YE3dKZjoqSqDU3DeRmMM7SUrhyYP15Exe554SLkgHu27wCiUtApunfghU3C3sXDPiUtigWg2s2qh5M72qtq2mm7G`

ORIGINAL DEV DONATION ADDRESS
Donations accepted at: `42QWoLF7pdwMcTXDviJvNkWEHJ4TXnMBh2Cx6HNkVAW57E48Zfw6wLwDUYFDYJAqY7PLJUTz9cHWB5C4wUA7UJPu5wPf4sZ`
