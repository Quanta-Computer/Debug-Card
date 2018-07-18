This firmware patch is to enable building firmware components required for Debug Card MCU functionality as defined in 
Debug Card design @ http://www.opencompute.org/wiki/Server/SpecsAndDesigns

Note: This patch is tightly dependent on various Texas Instrument's packages. Please read below for more info.

# Requirements:

- Need to have access to Windows Environment to run TI's Code Composer Studio

# Steps to setup Development Environment

1. Download and install Code Composer Studio fro TI's website. This example uses Ver: 5.5.077
2. Get the following source code package from TI: SW-DK-SMC-LM4FB1-1235-alpha
Note: Please make sure to work with TI to get this package and might need to sign and NDA to get access.

# Building BridgeIC Boot Firmware:

==================================
- On Windows Environment
1. Run Code Composer Studio.
2. Use Project->New CCS Project
3. Input Project Name: lcd_debug_card_bootloader_base
4. Choose Sys/BIOS->Typical
5. Press Finish
6. Delete following files from project directory lcd_debug_card_bootloader_base:
        - .ccsproject
        - .cproject
7. Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to lcd_debug_card_bootloader_base/
        - driverlib, inc, utils, third_party
8. Delete all the sub-folder under third_party besides:
        - third_party/uip-1.0/uip
9. Copy the lcd_debug_card_bootloader_base/ folder to Linux Environment

- On Linux Environment
1. Copy the following files to lcd_debug_card_bootloader_base/ directory:
        - driverlib.lib
        - lcd_debug_card_boot003.patch
        - lcd_debug_card_patch_boot003.sh
2. Run lcd_debug_card_patch_boot003.sh script to patch the directory with required changes
3. Copy the lcd_debug_card_bootloader_base/ directory back to Windows Environment

- On Windows Environment:
1. Build the boot firmware: Project->Build All
2. Find the boot firmware under directory: Binaries

# Building BridgeIC Run Time Firmware:

====================================
- On Windows Environment
1. Run Code Composer Studio.
2. Use Project->New CCS Project
3. Input Project Name: lcd_debug_card_base
4. Choose Sys/BIOS->Typical
5. Press Finish
6. Delete following files from project directory lcd_debug_card_base:
	- .ccsproject
	- .cproject
7. Create following two subfolders in lcd_debug_card_base:
	- chip
	- core 
8. Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to lcd_debug_card_base/chip
	- driverlib, inc
9. Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to lcd_debug_card_base/core
	- smclib, utils
10. Copy the lcd_debug_card_base/ folder to Linux Environment

- On Linux Environment
1. Copy the following files to lcd_debug_card_base/ directory:
	- lcd_debug_card_r013.patch
	- lcd_debug_card_r013_patch.sh
2. Run lcd_debug_card_r013_patch.sh script to patch the directory with required changes
3. Copy the lcd_debug_card_base/ directory back to Windows Environment

- On Windows Environment:
1. Build the run-time firmware: Project->Build All
2. Find the firmware binary under directory: Binaries

## Join the Debug Card MCU community
See the CONTRIBUTING file for how to help out.

## License
Debug Card MCU is BSD-licensed. We also provide an additional patent grant.
