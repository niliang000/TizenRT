# sidk_s5jt200

Samsung IoT Development Kit for S5JT200 chipset.

## Information

will be updated

## Environment Set-up
### For OpenOCD

on Ubuntu 13.10 ~ 14.xx version
```bash
sudo apt-get install -y lib32z1 lib32ncurses5 lib32bz2-1.0
```

on Ubuntu over 16.xx version
```bash
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1
```

### For FTDI

Install the package for usb
```bash
sudo apt-get install libusb-dev
```

Get the package, [libftdi-0.19](http://www.intra2net.com/en/developer/libftdi/download/libftdi-0.19.tar.gz)

Untar the downloaded package
```bash
tar -zxvf libftdi-0.19.tar.gz
```

Build and install the package for libftdi
```bash
cd libftdi-0.19
./configure
make
sudo make install
```

Link the built files
```bash
cd /usr/lib
sudo ln -s /usr/local/lib/libftdi.a libftdi.a
sudo ln -s /usr/local/lib/libftdi.la libftdi.la
sudo ln -s /usr/local/lib/libftdi.so.1.19.0 libftdi.so.1.19.0
sudo ln -s /usr/local/lib/libftdi.so.1.19.0 libftdi.so
sudo ln -s /usr/local/lib/libftdi.so.1.19.0 libftdi.so.1
```

### For FT2232 interface driver for OpenOCD

Get the package, [libftd2xxx1.0.4](https://github.com/psi46/HDItest/tree/master/FTDI-1.0.4/libftd2xx1.0.4)

Untar the downloaded package
```bash
tar -zxvf libftd2xx1.0.4.tar.gz
```

Copy and link the files
```bash
cd libftd2xx1.0.4
sudo cp ftd2xx.h /usr/include
sudo cp WinTypes.h /usr/include
sudo cp build/x86_64/libftd2xx.so.1.0.4 /usr/local/lib
cd /usr/local/include
sudo ln -s /usr/include/ftd2xx.h ftd2xx.h
sudo ln -s /usr/include/WinTypes.h WinTypes.h
cd /usr/local/lib
sudo ln -s libftd2xx.so.1.0.4 libftd2xx.so
cd /usr/lib
sudo ln -s /usr/local/lib/libftd2xx.so.1.0.4 libftd2xx.so
```

## Configuration Sets

There are three configuration sets for sidk_s5jt200, including 'tc', 'kernel_sample', and 'hello_with_tash'.
'tc' is a configuration set for runnig unit test cases, 'kernel_sample' for running kernel functions, and 'hello_with_tash' for running a hello example.
You can modify the configuration by using the menuconfig tool on the 'os' folder, but all configuration combinations are not fully tested yet.
The IPv4 network stack based on LWIP is included, but Wi-Fi related codes such as wpa_supplicant are not included.
Wi-Fi will be added in 2017.
