## Tool Installation 

### System Information
1. OS: Ubuntu 22.04
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
```
![Screenshot from 2024-06-06 20-50-06](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/cdb64531-ef3f-4d21-876b-dc78a66a2c56)

### iVerilog

```
sudo apt install iverilog
iverilog -v

```



![Screenshot from 2024-06-06 21-19-24](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/fe6a9b25-1ce5-4b62-a794-a58204a7db8f)



### GTKWave
```
sudo apt install gtkwave
gtkwave
```
![Screenshot from 2024-06-06 21-31-09](https://github.com/poudelbidhan/VSD-HDP/assets/69006235/3591863c-a35f-4237-ba05-f542f9ca4217)


### OpenSTA


    git clone https://github.com/parallaxsw/OpenSTA.git
    cd OpenSTA
    mkdir build
    cd build
    cmake ..
    make


![Screenshot from 2024-07-12 11-31-14](https://github.com/user-attachments/assets/7c2b41c0-3f5f-40e3-829e-5e2da43b7ae0)




