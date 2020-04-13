# INSTALLING ARDUINO IDE
## WINDOWS 10
There are currently three ways to install the Arduino IDE software on your windows PC. This guide is for users currently running Windows 10 and installation on previous versions of Windows is expected to be similar but is not guranteed.
1. Download and execute the installer (all Windows versions): the recommended way to go. The Installer installs also drivers but is only for when you have administrator rights on your Windows account.
2. Download the .zip archive (also all Windows versions): for when you have no administrator rights. You will have to install the drivers manually.
3. Download and install the IDE as an app from the Windows Store (Windows 10 only): this is quick and easy, but not recommended. This option will probably install an older version which probably has some issues.
###  1. USING EXECUTABLE INSTALLER
* First visit the official [Arduino website](https://www.arduino.cc/en/Main/Software) and download the Windows Installer executable file.

* This will open the following page:

* Choose "Just Download" or "Contribute and download".

* Start the .exe file you just downloaded. Choose “Yes” to trust the installer to make changes to your computer.  Then, agree to the License Agreement.

* Select the components to install (recommended to leave all selected).

* Choose the installation folder (recommended to keep the default) and click install.

* Wait for the installer to finish.

* Click Install to install the Adafruit driver.

* Click the Install button to install the USB driver.

Setup completed!

### 2. USING ZIP ARCHIVE

### 3. FROM WINDOWS STORE
* This is by far the easiest method but is not usually recommended since this downloads an outdated version and is known to have some compiler related bugs. But it's still a viable option for those who are just beginners.
Visit the [Microsoft Store official page](https://www.microsoft.com/en-us/p/arduino-ide/9nblggh4rsd8) and click on install to install the software.


--- ---
## UBUNTU 
Download the latest version of the Arduino IDE from the [Arduino website](https://www.arduino.cc/en/Main/Software) as a tarball.

In order to extract the files we need from the tarball, we can open a terminal, `cd` to where the downloaded tarball is, then run
```Shell
tar xvf arduino-(version number)-linux64.tar.xz
```
You can run ` ls ` to find the directory where the tarball is extracted and then `cd` to the directory.

Run `ls` again to ensure there is a file named `install.sh` inside the directory.

We need to give the file the required permissions to be executed so run.     
```Shell
chmod +x install.sh
```
Now run the installer.
```
./install.sh
```
If the script executes correctly and outputs `done!` at the end of its output, the IDE was installed correctly!

However we need to still workout some permission issues.

Before launching the IDE for the first time, connect your Arduino board to your computer with a USB cable.

The first time we launch Arduino, a window will pop up asking to add us to the `dialout` group:

Click on `Add`.

However the settings are currently not applied and you need to log out and log back in for the changes to to be applied.

Ensure you have your port available under `Tools/Serial Port`.

If the /ttyACM* port is still not available for flashing, here are several possible reasons why: 

*  The modem manager is using the port. When the port becomes active, the modem manager can claim the port, blocking the IDE's access to the port. The exact command to remove it will depend on your Linux distribution. For example, the command:

    ```
    sudo apt-get remove modemmanager
    ```
* The `/ttyACM` port was not created automatically when you plugged in your board. To add the port, do the following:
Create a file: `etc/udev/rules.d/50-arduino.rules`
Add the following to the file:
    ```
    KERNEL=="ttyACM[0-9]*", MODE="0666"
    ```
    Restart udev by entering the following command:
    ```
    sudo service udev restart   
    ```
* If you still are not able to see the port in the IDE, it may be because your user hasn't been added to the dialout group. Add yourself to the dialout group by entering the following command:
    ```
    sudo adduser your_user_name dialout       
    ```
    Then restart the IDE and try again.
    If you are using a virtual machine (VM), you may need to reboot Linux within the VM.

Setup Completed! 

