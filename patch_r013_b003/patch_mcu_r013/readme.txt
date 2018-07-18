Reference: https://github.com/facebook/BridgeIC

● Steps to setup Development Environment
1. Download and install Code Composer Studio fro TI's website. This example uses Ver: 5.5.077
2. Get the following source code package from TI: SW-DK-SMC-LM4FB1-1235-alpha Note: Please make sure to work with TI to get this package and might need to sign and NDA to get access.

● Building BridgeIC Run Time Firmware

    ***** On Windows Environment *****
    
    01. Run Code Composer Studio.
    02. Use Project->New CCS Project
    03. Input Project Name: lcd_debug_card_base
    04. Choose Sys/BIOS->Typical
    05. Press Finish
    06. Delete following files from project directory lcd_debug_card_base:
        .ccsproject
        .cproject
    07. Create following two subfolders in lcd_debug_card_base:
        chip
        core
    08. Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to lcd_debug_card_base/chip
        driverlib
        inc
    09. Copy the following folders from SW-DK-SMC-LM4FB1-1235-alpha to lcd_debug_card_base/core
        smclib
        utils
    10. Copy the lcd_debug_card_base/ folder to Linux Environment
    
    ***** On Linux Environment *****
    
    01. Copy the following files to lcd_debug_card_base/ directory:
        lcd_debug_card_r013.patch
        lcd_debug_card_r013_patch.sh
    02. Run lcd_debug_card_r013_patch.sh script to patch the directory with required changes
    03. Copy the lcd_debug_card_base/ directory back to Windows Environment
    
    ***** On Windows Environment *****
    
    1. Build the run-time firmware: Project->Build All
    2. Find the firmware binary under directory: Debug

