# SatNOGS Flowgraphs

SatNOGS GNU Radio flowgraphs.

## Installation

### Requirements

- CMake (> 3.8)
- GNU Radio (> 3.8.0)
- [gr-satnogs](https://gitlab.com/librespacefoundation/satnogs/gr-satnogs)
- [gr-soapy](https://gitlab.com/librespacefoundation/gr-soapy) (>= 2.0.0)

### Debian

Dependencies available via openSUSE Open Build Service in the repositories of the
[home:librespace:satnogs project](https://build.opensuse.org/repositories/home:librespace:satnogs).
When using those repositories, the dependencies can be installed with:

```
sudo apt-get install build-essential gnuradio-dev gr-satnogs
```

### Installation from Souce

```
git clone https://gitlab.com/librespacefoundation/satnogs/satnogs-flowgraphs.git
mkdir build
cd build
cmake ..
# make  # (unusual, but this step is *not* required in this project at the moment)
sudo make install
```

## License ##

[![license](https://img.shields.io/badge/license-GPL%203.0-6672D8.svg)](LICENSE)
[![Libre Space Foundation](https://img.shields.io/badge/%C2%A9%202020-Libre%20Space%20Foundation-6672D8.svg)](https://libre.space/)

