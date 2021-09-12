# xubuntu 20.04 - Desktop Configuration 

Configuration for Operating System Ubuntu 20.04 with Open Source Desktop XFCE4.

## Sources List 

```bash
## Repos Ubuntu 20.04
deb http://bo.archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
deb http://bo.archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb http://bo.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu focal-security main restricted universe multiverse

deb-src http://bo.archive.ubuntu.com/ubuntu/ focal main restricted universe multiverse
deb-src http://bo.archive.ubuntu.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://bo.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu focal-security main restricted universe multiverse

deb http://archive.canonical.com/ubuntu focal partner
deb-src http://archive.canonical.com/ubuntu focal partner
```

## Update and Install Packages 

```bash
## Update Operating System 
apt update
apt upgrade -y

## Installing required packages
apt install -y linux-headers-$(uname -r) build-essential checkinstall make \
automake cmake autoconf lsb-release dkms

## Intel Firmware and sensors controller
apt install -y intel-microcode intel-gpu-tools lm-sensors

## For lm-sensors
sensors-detect --auto

## Packages for compress and uncompress
apt install -y bzip2 zip unzip unace rar unace-nonfree p7zip p7zip-full \
p7zip-rar unrar unrar-free lzip lhasa arj sharutils mpack lzma lzop \
cabextract xz-utils

## Desktop Tools
apt install -y apt-transport-https ca-certificates curl \
gnupg-agent software-properties-common tuned tuned-gtk tuned-utils \
hardinfo arc-theme acpi acpid acpitool software-properties-common dirmngr

## Ubuntu extra tools
apt install -y ubuntu-restricted-extras xubuntu-icon-theme 

## Vim 
apt install -y vim vim-scripts vim-syntax-docker vim-syntax-gtk

## Sound tools
apt install -y alsa-base alsa-firmware-loaders alsa-oss alsa-tools alsa-utils
```

## Uninstall snap

```bash
## List and remove snap packages
snap list
snap remove <NAME_PACKAGE>

## Unmount snap point
umount /snap/core/<ID_INSIDE>
## or 
umount /var/snap

## Purge snap
apt purge snapd

## Remove snap files
rm -rf ~/snap
sudo rm -rf /snap
sudo rm -rf /var/snap
sudo rm -rf /var/lib/snapd
```

## Audio Codecs

```bash
## Codecs, Sound and Video
apt install -y vlc gstreamer1.0-libav gstreamer1.0-plugins-ugly gstreamer1.0-plugins-bad \
gstreamer1.0-pulseaudio vorbis-tools faac faad ffmpeg ffmpeg2theora
```

## Tipografías

```bash
## Fonts for OS
apt install -y ttf-mscorefonts-installer fonts-freefont-ttf fonts-freefont-otf
```

## Design

```bash
## Editor images
apt install -y gimp gimp-data-extras inkscape inkscape-open-symbols dia \
dia-rib-network dia-shapes dia-common blender blender-ogrexml-1.9
```

## Tools for DB

```bash
## SQLite3
apt install -y sqlitebrowser sqlmap sqlite3

## MariaDB
apt install software-properties-common dirmngr apt-transport-https
apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
add-apt-repository 'deb [arch=amd64] https://mirror.insacom.cl/mariadb/repo/10.5/ubuntu focal main'
## Update repos
apt update
apt upgrade -y
## Install MariaDB
apt install -y mariadb-server mariadb-client mycli
```

## Google Chrome

```bash
## Add repo
echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" | sudo tee /etc/apt/sources.list.d/google-chrome.list
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 78BD65473CB3BD13
## Update repo
apt update
## Install Web Browser
apt install -y google-chrome-stable
```

## Electronic Tools

```bash
apt install -y arduino arduino-core fritzing fritzing-parts
```

## VSCode

```bash
## Add repo
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
install -o root -g root -m 644 packages.microsoft.gpg /etc/apt/trusted.gpg.d/
rm packages.microsoft.gpg
sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/trusted.gpg.d/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list'
## Update repo
apt update
## Install packages
apt install apt-transport-https
apt install code
```

## Typora

```bash
## Add repo
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
add-apt-repository 'deb https://typora.io/linux ./'
## Update repo
apt-get update
## Install Package
apt-get install typora
```

## Extra tools

```bash
## Hardware detect
apt install hwinfo 

## Tools for video
apt install -y mesa-utils 

## Hacking tools
apt install -y crunch speedtest-cli etherape ettercap-text-only aircrack-ng wireshark \
nmap tcpdump testssl.sh stegosuite exiftool nikto whatweb sqlmap traceroute httrack \
hydra hydra-gtk chkrootkit hping3 fping masscan iftop

## Privileges
adduser $(whoami) wireshark
adduser $(whoami) tcpdump

## Varied tools
apt install -y peek putty putty-tools telegram-desktop transmission cheese figlet mlocate \
jq ghex gqrx-sdr terminator tree gparted gpart parted ntfs-3g exfat-fuse exfat-utils git \
curl wget whois telnet xscreensaver-gl xscreensaver-gl-extra golang-docker-credential-helpers \
keepassxc ssh-askpass ssh-askpass-gnome gromit-mpx

## Mail tools
apt install -y geary hunspell-es

## Development Languages and frameworks
apt install -y golang hugo

## Android tools
apt install -y android-tools-adb apkinfo apktool

## Java JDK and more
apt install -y default-jdk default-jre

## Gradle compiler
add-apt-repository ppa:cwchien/gradle

## Proxys
apt install -y tor torbrowser-launcher torsocks tor proxychains proxytunnel

## Obs Studio
apt install -y obs-studio obs-plugins

## Scan security server (rkhunter need postfix mail configuration)
apt install -y lynis chkrootkit rkhunter

## Python add
apt install -y python3-virtualenv python3-pip

## Icons themes
apt install -y adwaita-icon-theme-full obsidian-icon-theme numix-icon-theme

## Image resize
apt install -y optipng imagemagick
```

## Printers

```bash
## Packages printers
apt install -y cups cups-core-drivers cups-filters cups-filters-core-drivers cups-ipp-utils hplip hplip-data
```

## Remote server

```bash
## SSH server
apt install -y ssh openssh-server openssh-client mosh
```

## Firewall

```bash
apt install -y ufw
```

## KVM 

```bash
## KVM Virtualization
apt install -y qemu-kvm qemu-utils libvirt-clients libvirt-daemon-system \
virt-viewer virt-what virtinst virt-manager

## For privileges
adduser $(whoami) libvirt
adduser $(whoami) libvirt-qemu
adduser $(whoami) kvm
```

## VirtualBox

```bash
## Add repo
wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
echo "deb [arch=amd64] https://download.virtualbox.org/virtualbox/debian focal contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
## Update repo
apt update
## Install packages
apt install -y virtualbox-6.1

## Privileges
adduser $(whoami) vboxusers
```

## Docker-CE

```bash
## Install dependences
apt-get install apt-transport-https ca-certificates curl \
gnupg-agent software-properties-common

## Add keys
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

## Add repo
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable"

## Update repo
apt-get update

## Install packages 
apt-get install docker-ce docker-ce-cli containerd.io

## Privileges
adduser $(whoami) docker
```

## Docker Compose

```bash
## Download binary
curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

## Execute privilege
chmod +x /usr/local/bin/docker-compose
```

## Vagrant

```bash
## Install packages
apt install -y vagrant vagrant-digitalocean vagrant-libvirt
```

## Ansible

```bash
apt install -y ansible
```

## Terraform

```bash
## Add key
curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -

## Add repo
apt-add-repository "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main"

## Update repo
apt update

## Install package
apt install terraform
```

## Libreoffice 7

```bash
## Create file
vim /etc/apt/sources.list.d/libreoffice-7-focal.list
-- deb http://ppa.launchpad.net/libreoffice/libreoffice-7-0/ubuntu focal main
-- # deb-src http://ppa.launchpad.net/libreoffice/libreoffice-7-0/ubuntu focal main

## Add key and update 
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key_repo>
apt update
apt upgrade -y
```

## Chromium Browser no Snap

```bash
## Create file repo
vim /etc/apt/sources.list.d/xalt7x-chromium-vaapi.list 
-- deb http://ppa.launchpad.net/xalt7x/chromium-deb-vaapi/ubuntu focal main
-- # deb-src http://ppa.launchpad.net/xalt7x/chromium-deb-vaapi/ubuntu focal main

## Create pin file
vim /etc/apt/preferences.d/pin-xalt7x-chromium-deb-vaapi
-- Package: *
-- Pin: release o=LP-PPA-xalt7x-chromium-deb-vaapi
-- Pin-Priority: 1337

## Add key and update 
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys <key_repo>
apt update

## Install packages
apt install -y chromium-browser chromium-browser-l10n
```

## AWS CLI


## Dash Dock for Gnome

```bash
gsettings set org.gnome.shell.extensions.dash-to-dock extend-height false
```

## Comandos 

```bash
ubuntu-drivers devices
ubuntu-drivers autoinstall
nvidia-smi
```
