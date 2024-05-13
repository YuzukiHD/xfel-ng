

***
# XFEL -NG
Tiny FEL tools for allwinner SOC.

[Releases](https://github.com/xboot/xfel/releases/)

## Usage

```shell
usage:
    xfel version                                        - Show chip version
    xfel hexdump <address> <length>                     - Dumps memory region in hex
    xfel dump <address> <length>                        - Binary memory dump to stdout
    xfel read32 <address>                               - Read 32-bits value from device memory
    xfel write32 <address> <value>                      - Write 32-bits value to device memory
    xfel read <address> <length> <file>                 - Read memory to file
    xfel write <address> <file>                         - Write file to memory
    xfel exec <address>                                 - Call function address
    xfel reset                                          - Reset device using watchdog
    xfel sid                                            - Show sid information
    xfel jtag                                           - Enable jtag debug
    xfel ddr [type]                                     - Initial ddr controller with optional type
    xfel sign <public-key> <private-key> <file>         - Generate ecdsa256 signature file for sha256 of sid
    xfel spinor                                         - Detect spi nor flash
    xfel spinor erase <address> <length>                - Erase spi nor flash
    xfel spinor read <address> <length> <file>          - Read spi nor flash to file
    xfel spinor write <address> <file>                  - Write file to spi nor flash
    xfel spinand                                        - Detect spi nand flash
    xfel spinand erase <address> <length>               - Erase spi nand flash
    xfel spinand read <address> <length> <file>         - Read spi nand flash to file
    xfel spinand write <address> <file>                 - Write file to spi nand flash
    xfel spinand splwrite <split-size> <address> <file> - Write file to spi nand flash with split support
    xfel extra [...]                                    - The extra commands
```

## Build from source

### Linux platform

The xfel tools depends on the `libusb-1.0` library, you need to install `libusb-1.0-0-dev` before compile, for example in ubuntu:

```shell
sudo apt install libusb-1.0-0-dev
```

Then just type `make` at the root directory, you will see a binary program.

```shell
cd xfel
make
sudo make install
```

### Window platform

Windows adopts the cross-compilation method, to install the cross-compilation tool chain in Ubuntu, using:

```shell
sudo apt install mingw-w64
sudo apt install autoconf
sudo apt install libtool-bin
```
And build libusb for cross-compilation.

```shell
git clone https://github.com/libusb/libusb.git
cd libusb
./autogen.sh
./configure --host=i686-w64-mingw32 --prefix=/usr/i686-w64-mingw32/
make
sudo make install
```

Build xfel source code

```shell
cd xfel
CROSS=i686-w64-mingw32- make
```

For 64-bits windows, you can using `x86_64-w64-mingw32-` instead of `i686-w64-mingw32` above.

## License

MIT License

Copyright(c) 2007-2022 Jianjun Jiang <8192542@qq.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
