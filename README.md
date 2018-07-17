This firmware patch is to enable building firmware components required for BridgeIC functionality as defined in 1S server design @ http://www.opencompute.org/wiki/Server/SpecsAndDesigns

Note: This patch is tightly dependent on various Texas Instrument's packages. Please read below for more info.

Requirements:

Need to have access to Windows Environment to run TI's Code Composer Studio
Steps to setup Development Environment

Download and install Code Composer Studio fro TI's website. This example uses Ver: 5.5.077
Get the following source code package from TI: SW-DK-SMC-LM4FB1-1235-alpha Note: Please make sure to work with TI to get this package and might need to sign and NDA to get access.
Building BridgeIC Boot Firmware:

==================================

On Windows Environment
Run Code Composer Studio.
Use Project->New CCS Project
Input Project Name: f20_tmp
Choose Sys/BIOS->Typical
Press Finish
Delete following files from project directory f20_tmp: - .ccsproject - .cproject
Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to f20_tmp/ - driverlib, inc, utils, third_party
Delete all the sub-folder under third_party besides: - third_party/uip-1.0/uip
Copy the f20_tmp/ folder to Linux Environment
On Linux Environment
Copy the following files to f20_tmp/ directory: - src/boot-loader/boot110.patch - src/boot-loader/driverlib.lib - src/boot-loader/patch_boot110.sh
Run patch_boot110.sh script to patch the directory with required changes
Copy the f20_tmp/ directory back to Windows Environment
On Windows Environment:
Build the boot firmware: Project->Build All
Find the boot firmware under directory: Binaries
Building BridgeIC Run Time Firmware:

====================================

On Windows Environment
Run Code Composer Studio.
Use Project->New CCS Project
Input Project Name: f20_tmp
Choose Sys/BIOS->Typical
Press Finish
Delete following files from project directory f20_tmp:
.ccsproject
.cproject
Create following two subfolders in f20_tmp:
chip
core
Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to f20_tmp/chip
driverlib, inc
Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to f20_tmp/core
smclib, utils
Copy the f20_tmp/ folder to Linux Environment
On Linux Environment
Copy the following files to f20_tmp/ directory:
src/run-time/bic131.patch
src/run-time/patch_bic131.sh
Run patch_bic131.sh script to patch the directory with required changes
Copy the f20_tmp/ directory back to Windows Environment
On Windows Environment:
Build the run-time firmware: Project->Build All
Find the firmware binary under directory: Binaries
Join the BridgeIC community

See the CONTRIBUTING file for how to help out.

License

BridgeIC is BSD-licensed. We also provide an additional patent grant.
