# Software update introduction
## **Introduction**

!!! note "The currently available versions of the BLIKVM project are hosted in the release package of the github. The update software function needs to keep the device connected. There are currently two ways to update the software."
    * Method 1: Click the update button through the web interface, and the program will be updated automatically. Restart is required after the update.
    * Method 2: Manually run the script on the KVM terminal to update, and restart after the update.

!!! info "Common causes of upgrade errors"
    * The device is not connected to the network;
    * Network access to github is limited;

!!! warning "We strongly recommend performing the update while you are in close proximity to the BliKVM hardware you are upgrading.  The reason is if anything goes wrong you can intervene."
    * If you are familiar with command-line operations, we recommend manually updating so that you can monitor the command-line status in real time.
    * If the update is abnormal and the web interface cannot exit the update status, use ssh to the terminal can and restart to recover.

## **Manually run the script to update**

!!! info "In the terminal，If the current system terminal can see the ro keyword and it is a read-only system, it is necessary to use 'rw' to make the system writable."
    ```
    sudo -i
    cd /opt/bin/blikvm/
    git pull --rebase
    python3 /opt/bin/blikvm/script/update.py
    ```
   Observe the output of the terminal. When you see the message of successful upgrade, the terminal enters reboot, and the reboot takes effect.

!!! warning "If you are unable to update successfully due to network issues, you can download the latest release.tar.gz package on another PC with a stable network connection and follow the instructions below for installation."
    - download address: https://github.com/ThomasVon2021/blikvm/releases
    - v1 v2 v3 hardware use release.tar.gz
    - v4 hardware use release-h616-v4.tar.gz
    SSH into the device terminal and use `tar -zxvf release.tar.gz` to extract the release.tar.gz file.
    ```
    rw
    sudo -i
    cd /your release path/
    python3 install_release.py --releasepath=./
    ro
    ```
    You can compare the versions before and after in /usr/bin/blikvm/package.json. If you have upgraded to the specified version, the installation is successful, and you can reboot for the changes to take effect.
    
## **Web UI update**
!!! warning "The current web upgrade function is temporarily disabled. Please use the command line to update"

!!! info "After clicking the More Options button, find the CheckUpdate button and click it. If the available version is found, the pop-up box in the figure below will appear. Click OK to enter the upgrade process. The web interface is temporarily inoperable during the upgrade process. View the current update status by manually refreshing the page. When the message of successful update appears, it means that the update has been successful. Click the restart button, and the new version of software will take effect."
    ![IMG_8366](assets/images/update/update_button.png){width="300"}
    ![IMG_8366](assets/images/update/update_info.png){width="300"}
    ![IMG_8366](assets/images/update/upgrading.png){width="300"}
    ![IMG_8366](assets/images/update/update_reboot.png){width="300"}


