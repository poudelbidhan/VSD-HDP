# VSD-Hardware Design Program
## Week 0: Tool Installation 
### System Information
1. Linux: Ubuntu 22.04
2. RAM: 8 GB
3. Storage: 100 GB
4. Processor: 4 Core



### Yosys: Synthesis

```sh
sudo apt-get update
git clone https://github.com/YosysHQ/yosys.git
cd yosys
sudo apt install make # If make is not installed please install it
sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
make config-gcc
make 
sudo make install

