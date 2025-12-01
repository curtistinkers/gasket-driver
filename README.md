# Coral Gasket Driver

The Coral Gasket Driver allows usage of the [Coral EdgeTPU](https://coral.ai/)
on Linux systems. The driver contains two modules:

* Gasket: Gasket (Google ASIC Software, Kernel Extensions, and Tools) is a top
  level driver for lightweight communication with Google ASICs.
* Apex: Apex refers to the [EdgeTPU v1](https://coral.ai/technology)

This repo contains both the source for direct integration into a kernel tree as
well as the necessary files to generate a Debian DKMS package.

## Building the `.deb` package on Proxmox VE

From the top level directory, execute:

```sh
# Remove previously installed gasket drivers
sudo apt remove gasket-dkms

# Install build dependencies
sudo apt install git build-essential devscripts dkms dh-dkms proxmox-default-headers

# Clone this repo
git clone https://github.com/curtistinkers/gasket-driver

# Build the .deb file
cd gasket-driver && debuild -us -uc -tc -b
```

Install the resulting package using `dpkg -i` and reboot.
