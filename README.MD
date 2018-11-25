# Software installation instructions

### Summary:
1. [Disabling linux workstation automatic update](#1-disabling-linux-automatic-update)
2. [Default linux apps](#2-default-linux-apps)
3. [Firefox](#3-install-firefox-browser-and-plugins)
4. [Skype](#4-install-skype)
5. [Weather control](#5-weather-control)
6. [Storage on second hdd](#6-storage-on-second-hdd)
7. [Enable additional software repositories](#7-enable-additional-software-repositories)
8. [Install terminator](#8-terminator)
9. [Install java8](#9-install-java-8)


57. [Dropbox client](#57-dropbox-client)

----------
#### 1. Disabling linux automatic update

- Open file
```sudo vim /etc/apt/apt.conf.d/10periodic```

- change :
```APT::Periodic::Update-Package-Lists "1";```
- to : 
```APT::Periodic::Update-Package-Lists "0";```

[Back](#Summary:)

----------
#### 2. Default linux apps

- Copy this to terminal
```
sudo apt-get install -y tree
sudo apt-get install -y git
sudo apt-get install -y vim
sudo apt-get install -y openssh-server
sudo apt-get install -y alien
sudo apt-get install -y p7zip-full
sudo apt-get install -y aptitude
sudo apt-get install -y pandoc
sudo apt-get install -y sendmail
sudo sendmail config
```

[Back](#Summary:)

----------
#### 3. Install firefox browser and plugins

- Install firefox
- Install following plugins:
  - firessh
  - httprequester
  - pdfmage
  - text editor
  - simple youtube mp3 button
  - fireftp
  - youtube flash player
  
```
sudo apt-get install -y tree
sudo apt-get install -y git
sudo apt-get install -y vim
sudo apt-get install -y openssh-server
sudo apt-get install -y alien
sudo apt-get install -y p7zip-full
sudo apt-get install -y aptitude
sudo apt-get install -y pandoc
sudo apt-get install -y sendmail
sudo sendmail config
```

[Back](#Summary:)

----------
#### 4. Install skype

- Run the following commands from terminal:
  
```
sudo dpkg --add-architecture i386
sudo apt-get update
wget -O skype-install.deb http://www.skype.com/go/getskype-linux-deb
sudo dpkg -i skype-install.deb

sudo apt-get install -y skype 
```

[Back](#Summary:)

----------
#### 5. Install weather control

- Run the following commands from terminal:
  
```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install my-weather-indicator
```

Uses too much of system resources.

[Back](#Summary:)

----------
#### 6. Storage on second hdd

If necessary to create a partition use gparted: ```sudo apt-get install gparted``` 
During partition creation process select Device -> create partition table type -> gpt

[Back](#Summary:)

----------
#### 7. Enable additional software repositories

- Open terminal and enter command: ```sudo vim /etc/apt/sources.list```

- Remove hash (#) for remote repository entries (lines which start with # deb http...) and save file.

- Update repo metadata, upgrade system, clean up packages and clean cached files with command in terminal:
    ```
    sudo apt-get update;
    sudo apt-get dist-upgrade;
    sudo apt-get autoremove;
    sudo apt-get clean
    ```
    press Enter to confirm operations

[Back](#Summary:)

----------
#### 8. Terminator

- Copy this to terminal
```
sudo apt-get install -y terminator
```

[Back](#Summary:)

----------
#### 9. Install java 8

- Copy this to terminal
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
sudo apt-get install oracle-java8-set-default
export _JAVA_OPTIONS=-Xmx1024M
```
- Test result with command: ```java -version```

[Back](#Summary:)

----------



#### 57. Dropbox client

- Copy this to terminal
```
mkdir -p ~/bin
wget -O ~/bin/dropbox.py "https://www.dropbox.com/download?dl=packages/dropbox.py"
chmod +x ~/bin/dropbox.py

sudo apt install nautilus-dropbox
dropbox start -i

~/bin/dropbox.py start
```
Additional info
http://www.dropboxwiki.com/tips-and-tricks/using-the-official-dropbox-command-line-interface-cli

[Back](#Summary:)

----------