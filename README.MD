# Software installation instructions

### Summary:
1. [Disabling linux workstation automatic update](#1. disabling-automatic-update)
57. [Dropbox client](#57. dropbox-client)

----------
#### 1. Disabling automatic update

- Open file
```sudo vim /etc/apt/apt.conf.d/10periodic```

- change :
```APT::Periodic::Update-Package-Lists "1";```
- to : 
```APT::Periodic::Update-Package-Lists "0";```

[Back](#Summary:)

----------
#### 57. Dropbox client

mkdir -p ~/bin
wget -O ~/bin/dropbox.py "https://www.dropbox.com/download?dl=packages/dropbox.py"
chmod +x ~/bin/dropbox.py

sudo apt install nautilus-dropbox
dropbox start -i

~/bin/dropbox.py start

Additional info
http://www.dropboxwiki.com/tips-and-tricks/using-the-official-dropbox-command-line-interface-cli

[Back](#Summary:)

----------