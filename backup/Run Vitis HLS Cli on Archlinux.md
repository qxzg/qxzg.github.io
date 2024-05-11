### 1. Can't lunch vit_hls with error: `@E cannot exec arch command, error: couldn't execute "arch": no such file or directory`
run `echo "#\!bin/sh\nuname -m" > /usr/bin/arch; chmod +x /usr/bin/arch`

### 2. Can't run `csim_design`
Error log:
```
NFO: [SIM 211-2] *************** CSIM start ***************
INFO: [SIM 211-4] CSIM will launch GCC as the compiler.
   Generating csim.exe
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: /usr/lib/libm.so.6: unknown type [0x13] section `.relr.dyn'
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: skipping incompatible /usr/lib/libm.so.6 when searching for /usr/lib/libm.so.6
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: cannot find /usr/lib/libm.so.6
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: /usr/lib/libm.so.6: unknown type [0x13] section `.relr.dyn'
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: skipping incompatible /usr/lib/libm.so.6 when searching for /usr/lib/libm.so.6
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: /usr/lib/libmvec.so.1: unknown type [0x13] section `.relr.dyn'
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: skipping incompatible /usr/lib/libmvec.so.1 when searching for /usr/lib/libmvec.so.1
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: cannot find /usr/lib/libmvec.so.1
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: /usr/lib/libmvec.so.1: unknown type [0x13] section `.relr.dyn'
/opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld: skipping incompatible /usr/lib/libmvec.so.1 when searching for /usr/lib/libmvec.so.1
collect2: error: ld returned 1 exit status
make: *** [Makefile.rules:323: csim.exe] Error 1
ERROR: [SIM 211-100] 'csim_design' failed: compilation error(s).
INFO: [SIM 211-3] *************** CSIM finish ***************
```
Solution from https://support.xilinx.com/s/question/0D54U00005VQKeNSAX/vitis-hls-20211-ld-linker-and-libm-relr-section-error?language=en_US: 
Run `sudo mv /opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld /opt/Xilinx/Vivado/2022.2/tps/lnx64/binutils-2.37/bin/ld.back` to forces Vitis to use /usr/bin/ld