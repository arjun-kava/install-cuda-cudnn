# Installation process for CUDA and CuDNN

## Verify Capacity of GPU
`lspci | grep -i nvidia`

## Check supported version of linux
`uname -m && cat /etc/*release`

## verify gcc and make installed in system
`gcc --version # if failed execute sudo apt install gcc`

`make --version # if failes execute sudo apt install make`

## check version of kernel and install headers
`uname -r`

`sudo apt-get install linux-headers-$(uname -r)`

## blacklist nouveau drivers
`echo "blacklist nouveau" >> /etc/modprobe.d/blacklist-nouveau.conf`

`echo "options nouveau modeset=0" >> /etc/modprobe.d/blacklist-nouveau.conf`

## Regenerate kernel initrampfs
`sudo update-initramfs -u`

## Remove preinstalled drivers
`sudo apt-get purge nvidia-cuda*`

`sudo apt-get purge nvidia-*`

## Download Compatible driver .run file
[https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)

## Log in with `init 3` and install drivers
`init 3`

`cd Downloads`

`./your-nividia-driver.run # skip OpenGL installation and create cuda link while installation`


## After Installation 
`export PATH=/usr/local/cuda-x.x/bin${PATH:+:${PATH}}`

`export LD_LIBRARY_PATH=/usr/local/cuda-x.x/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}`

`export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-x.x/lib64`

`sudo ldconfig /usr/local/cuda-x.x/lib64`


