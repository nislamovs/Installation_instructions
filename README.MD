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
10. [Install maven3](#10-install-maven-3)
11. [Install google chrome](#11-install-google-chrome)
12. [Install MongoDB](#12-install-mongodb)
13. [Install power management utils](#13-install-power-management-utils)
14. [Install Postgresql database](#14-install-postgresql-database)
15. [Install grsync](#15-install-grsync)
16. [Install MySql database](#16-install-mysql-database)
17. [Install telegram](#17-install-telegram)


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
sudo apt-get install -y trash
sudo apt-get install -y htop
sudo apt-get install -y meld
sudo apt-get install -y tasksel
sudo apt-get install -y openssh-server
sudo apt-get install -y alien
sudo apt-get install -y filezilla
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
#### 10. Install maven 3

- If necessary uninstall maven2: ```sudo apt-get purge maven```

- Add this to /etc/apt/sources.list
```
deb http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main
deb-src http://ppa.launchpad.net/natecarlson/maven3/ubuntu precise main
```

- Then run command:
```
sudo apt-get update
sudo apt-get install maven3
sudo apt install maven
```

[Back](#Summary:)

----------
#### 11. Install google chrome

- Run the following commands from terminal:

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
sudo apt-get update
sudo apt-get install google-chrome-stable
```

[Back](#Summary:)

----------
#### 12. Install mongodb

- Run the following commands from terminal:

```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6
echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list

sudo apt-get update
sudo apt-get install -y mongodb-org
```

[Back](#Summary:)

----------
#### 13. Install power management utils

- Run the following commands from terminal:

```
sudo apt-get install powermanagement-interface
sudo pm-suspend
sudo pm-hibernate
```

[Back](#Summary:)

----------
#### 14. Install postgresql database

Installation of postresql db server, client(pgAdmin) and creating of test db.

Additional info: 

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-14-04

- Run the following commands from terminal:

```
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
sudo apt-get install pgadmin3
```
- Create test database:
```
sudo -i -u postgres
psql
CREATE DATABASE testdb;
CREATE TABLE playground (
    equip_id serial PRIMARY KEY,
    type varchar (50) NOT NULL,
    color varchar (25) NOT NULL,
    location varchar(25) check (location in ('north', 'south', 'west', 'east', 'northeast', 'southeast', 'southwest', 'northwest')),
    install_date date
);
#Show table
\d
#or
\dt
#exit
\q
#exit from user 
exit
```

[Back](#Summary:)

----------
#### 15. Install qrsync

Installation of qrsync (rsync with gui)

- Run the following commands from terminal:

```
sudo apt-get install grsync
```

[Back](#Summary:)

----------
#### 16. Install mysql database

Installation of mysql db server, db client, creating of test db.

Additional info: 

https://www.linode.com/docs/databases/mysql/install-mysql-on-ubuntu-14-04

- Check yout hostname:
```
hostname -f
```

- Run the following commands from terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-server

pass : root
```

- Creating test db:

```
mysql -u root -p

create database testdb;
create user 'perkele'@'localhost' identified by '81126f0afcf5a95115f397567f1066d1';
grant all on testdb.* to 'perkele';
use testdb;
create table customers (customer_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY, first_name TEXT,last_name TEXT);
```

- Restart service:

```
sudo service mysql stop
sudo dpkg-reconfigure mysql-server-5.5
sudo service mysql start
```

- Additional setup:

To make connections for external servers to db, run: 

```
sudo vim /etc/mysql/my.cnf
```
Change line:
```bind-address = 127.0.0.1```
to :
```bind-address = 0.0.0.0```

- Installation of Mysql Workbench

```sudo apt-get install mysql-workbench```

For ubuntu 16.04 download deb file from mysql site.

- Mysql performance tuner setup:

```
sudo apt-get install mysqltuner
```

[Back](#Summary:)

----------
#### 17. Install telegram

Installation of telegram

- Run the following commands from terminal:

```
sudo add-apt-repository ppa:atareao/telegram
sudo apt-get update
sudo apt-get install telegram
sudo apt-get install orville-write
```

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