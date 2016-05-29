#Summary
This is a project based on [lpc17xx.cmsis.driver](https://www.lpcware.com/content/nxpfile/lpc175x6x-cmsis-compliant-standard-peripheral-firmware-driver-library-keil-iar-gnu). I modified the the makefile and some files to build in unix environment. See change log for further info.

#How to build
Make sure you have this packages: `rmdir, makedepend, astyle`.

Eidt `makeconfig` file accordingly. 

`cd` to project directory and run `make`. This will create `DriverLPC17xxgnu.a` under `Driver/library` directory. You can now build examples inside `Examples` directory.

#Change log
##source code changes
- Chage `startup_lpc17xx.s` file line 147. The `_start` symbol has changed to main.

##make files changes
- Change all backslash (\) path separators to slash (/)
- Change make reciepe with reference to `rm`. Wildcard must be used without double qutations.
- Since we are building in unix shell there is no need for `BUILD_TOOL` in `make.rules.environment`.

##linker script changes
- Comment out library linkage line starts with `GROUP(...)` 