# Instructions

> These instructions are worked through in this [video](https://youtu.be/f09Hq6PxaRQ), which is why not everything is described here down to the last detail.

1. Install Homebrew

    Go to [Homebrew Github](https://github.com/Homebrew/brew/releases/) and download the .pkg file

    - install the downloaded package
    - after installation open terminal and add this:
        
        ```
        echo 'export PATH="/opt/homebrew/bin:$PATH"' >> ~/.zshrc
        ```

        ```
        source ~/.zshrc
        ```

---

2. Install Dotnet8 SDK

    [Dotnet8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

---

3. Install Database and other needed parts

    - go to [FlyEnv](https://flyenv.com/download.html) download and install the version for your system

    - after installation open FlyEnv and install required parts
        + php
        + mariadb
        + apache

---

4. Create a Database for Opensim

    - open phpmyadmin in FlyEnv (username and password: root)

---

5. Download OpenSim

    - you can download this package from this repo, from opensimulator.org, osgrid.org or other sites

    > This repo has the libgdiplus.dylib for macos integrated

---

6. move the file wherever you want and unzip it

---

7. edit config files

    > If you have a running opensim instance and just want to update it, just copy the opensim.ini and the config-include folder to the folder you just unziped.
    
    - open a terminal by the bin folder and write this commands

    ```
    cp OpenSim.ini.example OpenSim.ini
    ```

    ```
    cp config-include/StandaloneCommon.ini.example config-include/StandaloneCommon.ini
    ```

    - now edit the StandaloneCommon.ini (there are many options to do this, i will use nano in the terminal)

    ```
    nano config-include/StandaloneCommon.ini
    ````

    Since we want to use mariadb we have to deactivate the entry for SQLite, activate the entries for mysql and adjust the access data to the database.

---

8. Un-quarantine some files and add mono

    ```
    brew install mono-libgdiplus
    ```

    ```
    xattr -r -d com.apple.quarantine lib64/
    ```
    ```
    xattr -r -d com.apple.quarantine libgdiplus.dylib
    ```
---

9. start your opensim instance

    ```
    dotnet Opensim.dll
    ```
