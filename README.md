#Summary
This is a project based on [lpc17xx.cmsis.driver](https://www.lpcware.com/content/nxpfile/lpc175x6x-cmsis-compliant-standard-peripheral-firmware-driver-library-keil-iar-gnu). I modified the the makefile and some files to build in unix environment. See change log for further info.

#How to build

Make sure you have this packages: `rmdir, makedepend, astyle`.

Eidt `makeconfig` file accordingly. 

`cd` to project directory and run `make`. This will create `DriverLPC17xxgnu.a` under `Driver/library` directory. You can now build examples inside `Examples` directory.

##Toolchain
I build the source code successfully using Codesourcery lite bineries [arm-2013.05-23-arm-none-eabi.osx.intelx86.bin](http://www.carlson-minot.com/available-arm-eabi-g-lite-builds-for-mac-os-x) for mac.

I also build the project with (GCC ARM Embedded)[https://launchpad.net/gcc-arm-embedded] version 5.3.1. You will get an linker error `undefined symbol _start`. You can add `libnosys.a` library to linker script which solve the linker problem however, debuging project does not work properly.


#Change log
##source code changes
- Chage `startup_lpc17xx.s` file line 147. The `_start` symbol has changed to `main`.

##make files changes
- Change all backslash (\\) path separators to slash (/)
- Change make reciepe with reference to `rm`. Wildcard must be used without double qutations.
- Since we are building in unix shell there is no need for `BUILD_TOOL` in `make.rules.environment`.

##linker script changes
- Comment out library linkage line starts with `GROUP(...)` 