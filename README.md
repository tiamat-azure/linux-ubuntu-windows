For better User eXperience check Website : [tiamat-azure.github.io][site]

# Linux UBUNTU on Windows 10 (WSL)

![Header](img/header.jpg)

This project is intended to log software, libraries and frameworks installation on Linux UBUNTU 18 Windows Subsystem.


# Install Linux UBUNTU in WSL 2

```bash
# check Windows version
ver

Microsoft Windows [version 10.0.18362.476]

# check PowerShell version
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.18362.145
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.18362.145
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1

```

Source : 
- PowerShell 6 install : 
  - doc : https://docs.microsoft.com/fr-fr/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6
  - git url for PowerShell-6.2.3-win-x64.msi : https://github.com/PowerShell/PowerShell/releases/tag/v6.2.3  

    msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1

Install PowerShell 6 :

```bash
    # One liner install
    iex "& { $(irm https://aka.ms/install-powershell.ps1) } -UseMSI"

    # Check PowerShell version (from PS 6 Application))
    $PSVersionTable

    Name                           Value
    ----                           -----
    PSVersion                      6.2.3
    PSEdition                      Core
    GitCommitId                    6.2.3
    OS                             Microsoft Windows 10.0.19025
    Platform                       Win32NT
    PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
    PSRemotingProtocolVersion      2.3
    SerializationVersion           1.1.0.1
    WSManStackVersion              3.0
```

> Alternative install
>   - doc : https://docs.microsoft.com/fr-fr/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-6
>  - git url for PowerShell-6.2.3-win-x64.msi : https://github.com/PowerShell/PowerShell/releases/tag/v6.2.3  
>
>```bash
>msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
>```


WSL2 install documentation : 
  - https://docs.microsoft.com/en-us/windows/wsl/wsl2-install
  - [install-wsl-2-on-windows-10](https://www.thomasmaurer.ch/2019/06/install-wsl-2-on-windows-10/)

Enable the Windows Subsystem for Linux

    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

Install a Linux distro for the Windows Subsystem for Linux

Enable the Virtual Machine Platform feature

    Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform

Set WSL distro to use version 2
```bash
# List Linux distro installed
wsl -l -v

# Set Ubuntu-18.04 Linux distro to use WSL 2
wsl --set-version Ubuntu-18.04 2

# Set WSL 2 as the default version to use for futur Linux distro installation
wsl --set-default-version 2
```
# Update Linux packages

> Doc : [install-updates-on-ubuntu-via-command-line](https://tecadmin.net/install-updates-on-ubuntu-via-command-line/)

```bash
# Fetch the update for all your repositories
sudo apt update

# Upgrade all the packages to latest available versions
sudo apt-get upgrade

# Handle changing dependencies and remove obsolete package
sudo apt-get dist-upgrade

# Apply security updates only
sudo apt-get install unattended-upgrades
```

# Install Java

> Doc : [how-to-install-java-with-apt-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-18-04)

```bash
# Check java version
java -version

# Install openjdk 8 and 11
sudo apt install openjdk-8-jre-headless -y
sudo apt install openjdk-8-jdk-headless -y
#sudo apt install openjdk-11-jre-headless -y
#sudo apt install openjdk-11-jdk-headless -y

# Check java version
java -version

openjdk version "1.8.0_222"
OpenJDK Runtime Environment (build 1.8.0_222-8u222-b10-1ubuntu1~18.04.1-b10)
OpenJDK 64-Bit Server VM (build 25.222-b10, mixed mode)

# Check javac version
javac -version

javac 1.8.0_222

# Managing JVM versions installed
sudo update-alternatives --config java
sudo update-alternatives --config javac
```


# Configure Git

```bash
git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe" \
&& git config --global user.name "Tiamat" \
&& git config --global user.email "tiamat.azure@gmail.com"
```

# Install nvm

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash

# Apply profile
source .bashrc

# Install node versions (latest and LTS)
nvm install v12.13.0
nvm use v12.13.0
nvm install v13.1.0

# Check version
nvm --version && node -v && npm -v

0.35.1
v12.13.0
6.12.0
```

# Install Java

> Doc : [install-and-manage-multiple-java-versions-on-linux-using-alternatives](https://dev.to/thegroo/install-and-manage-multiple-java-versions-on-linux-using-alternatives-5e93)



# Install Docker

Excellent blog reading : [docker-running-seamlessly-in-windows-subsystem-linux](https://medium.com/faun/docker-running-seamlessly-in-windows-subsystem-linux-6ef8412377aa)








[jhi]: https://www.jhipster.tech/
[sb]: https://spring.io/projects/spring-boot
[ng]: https://angular.io/
[site]: https://tiamat-azure.github.io/linux-ubuntu-windows/