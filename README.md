<!-- PipeWire-Debian-->

<p align="center">
  <a href="https://gitlab.freedesktop.org/pipewire/pipewire">
    <img alt="PipeWire Original Repo" src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/logo/PipeWire_logo.png" width="656" height="300">
  </a>
</p>

<p align="center">
  <!-- Maintained -->
  <a href="https://github.com/pipewire-debian/pipewire-debian/">
    <img src="https://img.shields.io/website?down_message=Yes&label=Maintained&logo=GITHUB&up_message=Yes&url=https%3A%2F%2Fgithub.com%2Fpipewire-debian%2Fpipewire-debian">
  </a>
  <!-- Last commit on dev -->
  <a href="https://github.com/pipewire-debian/pipewire-debian/tree/development">
    <img src="https://img.shields.io/github/last-commit/pipewire-debian/pipewire-debian/development?color=%23ffA000&label=Last%20commit%20on%20Development&logo=GITHUB&style=plastic">
  </a>
  <!-- Last commit on master -->
  <img src="https://img.shields.io/github/last-commit/pipewire-debian/pipewire-debian/master?color=%23ffA000&label=master&logo=GITHUB&style=plastic">
  <!-- Packager -->
  <a href="https://github.com/souravdas142/">
    <img src="https://img.shields.io/website?down_message=Sourav%20Das&label=Packager&logo=GITHUB&up_message=Sourav%20Das&url=https%3A%2F%2Fgithub.com%2Fsouravdas142">
  </a>
</p>

<p align="center">
  <!-- Website status -->
  <a href="https://pipewire-debian.github.io/pipewire-debian/">
    <img src="https://img.shields.io/website?label=Git%20Website&logo=GITHUB&url=https%3A%2F%2Fpipewire-debian.github.io%2Fpipewire-debian%2F">
  </a>
  <!-- PPA -->
  <a href="https://launchpad.net/~pipewire-debian/+archive/ubuntu/pipewire-upstream">
    <img src="https://img.shields.io/github/v/tag/pipewire-debian/pipewire-debian?label=LP%20PipeWire%20PPA&logo=Ubuntu">
  </a>
  <!-- Project License -->
  <a href="https://choosealicense.com/licenses/mit/">
    <img alt="MIT License" src="https://img.shields.io/github/license/pipewire-debian/pipewire-debian">
  </a>
</p>

# PipeWire & blueman-git PPA for Ubuntu (>= 18.04)
#### _An upstream version of blueman-git & PipeWire for Ubuntu maintained with a 15 day release cycle_

|                                               Link                                               |          Description     |
| :----------------------------------------------------------------------------------------------: | :----------------------: |
|          [Original-PipeWire-Upstream](https://gitlab.freedesktop.org/pipewire/pipewire)          |        **Forked**        |
| [PipeWire-debian-Upstream](https://salsa.debian.org/utopia-team/pipewire/-/tree/debian/0.3.25-1) |        **Forked**        |
|            [Original-blueman-Upstream](https://github.com/blueman-project/blueman)               |        **Forked**        |
|            [blueman-debian-Upstream](https://salsa.debian.org/cschramm/blueman)                  |        **Forked**        |
|                  [libfdk-aac[12]](https://packages.ubuntu.com/hirsute/libfdk-aac2)               |     **Dependencies**     |
|                 [libopenaptx0](https://packages.ubuntu.com/hirsute/libopenaptx0)                 |     **Dependencies**     |
|               [libldacbt-abr2](https://packages.ubuntu.com/hirsute/libldacbt-abr2)               |     **Dependencies**     |
|               [libldacbt-enc2](https://packages.ubuntu.com/hirsute/libldacbt-enc2)               |     **Dependencies**     |

## [Launchpad PPA](https://launchpad.net/~pipewire-debian/+archive/ubuntu/pipewire-upstream)

<img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/warning.svg" width=22 height=22>&nbsp; **This repo (`master` branch which is <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/deprecated.svg" width=96 height=13> ) Can be viewed as a mirror of Launchpad PPA. I will keep sync this with the LP PPA. As this is `deprecated` use [this secion](#add-the-launchpad-ppa) section alternatively.** 

<img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/information.svg" width=28 height=28>&nbsp; **The [development](https://github.com/pipewire-debian/pipewire-debian/tree/development) branch is important as I will be using that branch to push new patches related to building PipeWire, blueman-git and their dependencies.**

## 1. PPA Configuration

### Add the Launchpad PPA...       

<img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/idea_bulb.svg" width=22 height=22> **The recommended & convenient way**

```bash
# You can update your system with unsupported packages from this untrusted PPA by adding ppa:pipewire-debian/pipewire-upstream
# to your system's Software Sources.

sudo add-apt-repository ppa:pipewire-debian/pipewire-upstream
sudo apt-get update

# This PPA can be added to your system manually by running below commands, It directly create 
# a file under /etc/apt/sources.list.d/ containing source mirror list. 
# First Download key from keyservers directly into the trusted set of keys, Run 2 commands below.

gpg --keyserver keyserver.ubuntu.com --recv-keys 25088A0359807596
gpg -a --export 25088A0359807596 | sudo apt-key add -

# Or, 

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 25088A0359807596

echo "deb http://ppa.launchpad.net/pipewire-debian/pipewire-upstream/ubuntu $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list.d/pipewire-upstream.list

# For Non ubuntu Debian based Users, Edit `/etc/apt/sources.list.d/pipewire-upstream.list` and change your `distro_code_name` equivalent to any one of ubuntu 
# `distro_code_name`. (For example, MX Linux 19.4 based on Debian buster, And equivalent to `ubuntu 18.04`, so replace `buster` with `bionic` in the mentioned file.)

# Below is generaly not required unless you are not inspecting a package or not thinking about repackaging from the source.

echo "deb-src http://ppa.launchpad.net/pipewire-debian/pipewire-upstream/ubuntu $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list.d/pipewire-upstream.list
```

### ...or the Github PPA  &nbsp; &nbsp; <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/deprecated.svg" width=128 height=17>

<img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/idea_bulb.svg" width=22 height=22> **Use IFF you have a good reason Or If your distro (other debian based) Can't install from LP PPA.**           

```bash
curl -SsL https://pipewire-debian.github.io/pipewire-debian/ubuntu/KEY.gpg | sudo apt-key add -
sudo curl -SsL -o /etc/apt/sources.list.d/pipewire.list https://pipewire-debian.github.io/pipewire-debian/ubuntu/pipewire.list
sudo apt update

```

## 2. Install PipeWire Or blueman-git

### After adding one of the PPA's, follow the installation instructions below

**For MX Linux or Debian buster see [this](https://pastebin.com/S5duuECS) for which packages are to be insalled or upgraded.**

```bash
# Install dependencies

sudo apt install libfdk-aac2 libldacbt-{abr,enc}2 libopenaptx0

# If `libfdk-aac2` not found install `libfdk-aac1`
# Install pipewire and additional packages

sudo apt install gstreamer1.0-pipewire libpipewire-0.3-{0,dev,modules} libspa-0.2-{bluetooth,dev,jack,modules} pipewire{,-{audio-client-libraries,pulse,media-session,bin,locales,tests}}

# Additionally, if you want to install `pipewire-doc`

sudo apt install pipewire-doc     


# ~~~~~~~~~~~~~ For blueman-git  ~~~~~~~~~~~~~~~          

# Before installing blueman-git, remove and purge any official version of blueman.        

sudo apt-get remove --purge blueman && sudo rm -f /var/lib/blueman/network.state

# Then, to install issue below command.

sudo apt-get install blueman-git         
```   

    
## 3. Post Installation Steps for PipeWire or blueman-git        
You don't need to uninstall PulseAudio to enable PipeWire, disable and mask PulseAudio related services to stop them    
```bash
systemctl --user --now disable  pulseaudio.{socket,service}
systemctl --user mask pulseaudio        
```
**Additional steps for ubuntu 18.04 Or Equivalent distros**        

```bash        
# You need to tell Pulseaudio not to respawn itself by issuing this command:     

sed -i 's/.*autospawn.*/autospawn = no/g' ~/.config/pulse/client.conf        

# If `~/.config/pulse/client.conf` not found then issue this,       

sudo sed -i 's/.*autospawn.*/autospawn = no/g' /etc/pulse/client.conf        

# Additonally if `/etc/pulse/client.conf.d/00-enable-autospawn.conf` this file exist do (Mx Linux)

sudo sed -i 's/.*autospawn.*/autospawn = no/g' /etc/pulse/client.conf.d/00-enable-autospawn.conf       

# Also If `/etc/xdg/autostart/pulseaudio.desktp` file exist, you have to backup this file to somewhere or have to delete it.

# And finally issue        

pulseaudio --kill        
```        

**For Mx Linux Or `init` system**

<pre>
<code>
# Mx Linux uses init system by default, Anyone using `systemd` ignore this section.

# Some users feel anoying to start `pipewire` services becasue of PW doesn't shift any scripts for non systemd, So Now how to start 
# All `pipewire` services in init system?

# There is a solution on internet see this : <a href="https://www.linuxquestions.org/questions/slackware-14/using-pipewire-instead-of-pulseaudio-in-slackware-15-a-4175693980">Slackware Solution</a> the idea is same for Mx Linux also

# For the above solution you have to install <a href="https://github.com/raforg/daemon">daemon program</a> or do the below modifcation on those `.desktop` files.

substitue this `Exec=/usr/bin/pipewire` line with above `pipewire.desktop` file where you find lines starting with `Exec`. 
substitue this `Exec=/usr/bin/pipewire-pulse` line with above `pipewire-pulse.desktop` file where you find lines starting with `Exec`. 
substitue this `Exec=/usr/bin/pipewire-media-session` line with above `pipewire-media-session.desktop` file where you find lines starting with `Exec`. 


</code>
</pre>

<img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/warning.svg" width=22 height=22>&nbsp; **Since version `0.3.28` conf files are moved to `/usr/share/` directory from `/etc/`.  You have to copy them to `/etc/` directory manually. From Now `/etc/pipewire/` can be used as system wide drop in for User edited conf files. `conffile` overridden behaviour is `$HOME/.config/pipewire > /etc/pipewire > /usr/share/pipewire`**              

To copy conffiles from `/usr/share/` to `/etc/`, issue below command. **(Optional)**     

```bash
sudo cp -vRa /usr/share/pipewire /etc/
```

Enable and start PipeWire related services **(`init` system users, Ignore this)**       
```bash
systemctl --user --now enable pipewire{,-pulse}.{socket,service} pipewire-media-session.service
```
You can check which server is in use by running (as a user):   
```bash
pactl info | grep '^Server Name'
```
If your system doesn't have any sound, please reboot    

Incase of blueman, just enable below service. **(`init` system users, Ignore this)**
```bash
sudo systemctl enable --now blueman-mechanism.service
```



# <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/open_book.svg" width=48 height=48> Wiki

- [This Repo Wiki](https://github.com/pipewire-debian/pipewire-debian/wiki)
- [Upstream-README](https://gitlab.freedesktop.org/pipewire/pipewire/-/blob/master/README.md)
- [Upstream-wiki](https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/home)
- [Upstream-blueman-wiki](https://github.com/blueman-project/blueman/wiki)
- **Gentoo**
    - [Gentoo-wiki](https://wiki.gentoo.org/wiki/PipeWire)
    - [Gentoo-Bluetooth-Wiki](https://wiki.gentoo.org/wiki/Bluetooth)
- **Arch-Linux** 
    - [Arch-wiki](https://wiki.archlinux.org/index.php/PipeWire)
    - [Arch-Bluetooth-Wiki](https://wiki.archlinux.org/title/Bluetooth)
    - [blueman](https://wiki.archlinux.org/title/Blueman)
- [Debian-wiki](https://wiki.debian.org/PipeWire) &nbsp; &nbsp; &nbsp; **[ <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/deprecated.svg" width=96 height=13>  for this PPA ]**

# <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/wrench_and_hammer.svg" width=48 height=48> Troubleshooting  

**See in wiki page - [Troubleshooting](https://github.com/pipewire-debian/pipewire-debian/wiki/Troubleshooting)**

# <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/flame.svg" width=48 height=48> Notice

If you have any issue regarding this PPA package, create a issue here.

**For features, requests or bugs, create an issue on [upstream](https://gitlab.freedesktop.org/pipewire/pipewire/-/issues) For PW**
**And for blueman on [here](https://github.com/blueman-project/blueman/issues/new)**    

# <img src="https://raw.githubusercontent.com/wiki/pipewire-debian/pipewire-debian/images/icons/clap.svg" width=48 height=48> Credits

Original PipeWire project maintainer:
[Wim Taymans](https://gitlab.freedesktop.org/wtaymans) - [Source](https://gitlab.freedesktop.org/pipewire/pipewire)

Original maintainers (usually from Debian):
Utopia Maintenance Team - Jeremy Bicha - [Source](https://salsa.debian.org/utopia-team/pipewire/-/tree/debian/0.3.25-1)      

Original blueman project maintainer:
[Christopher Schramm](https://github.com/cschramm) - [Source](https://github.com/blueman-project/blueman)   



