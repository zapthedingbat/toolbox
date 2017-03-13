# Toolbox #

A little compendium of tools, references and resources for web development in a mostly windows environment
These are windows, or cross platform tools

## Development ##
- [.Net core](https://www.microsoft.com/net/core)
    Cross platform runtime environment and compiler for .Net
- [Python](https://www.python.org/)
    Python programing language and runtime environment.
- [NodeJs](https://nodejs.org/)
    JavaScript runtime environment.

## Applications ##
- [Chrome](https://www.google.com/chrome/)
    Google chrome web browser.
- [FireFox](https://www.mozilla.org/en-GB/firefox/new/)
    Mozilla FireFox web browser.
- [InkScape](https://inkscape.org/)
    Vector graphics editor.
- [Notepad++](https://notepad-plus-plus.org/)
    Source code editor and Notepad replacement.
- [Paint.net](http://www.getpaint.net/)
    Image and photo editor.
- [Tor Browser](https://www.torproject.org/)
    Tor based web browser for anonymous communication and browsing.
- [VirtualBox](https://www.virtualbox.org/)
    General-purpose virtualizer to host other operating systems.
- [VisualStudio Code](https://code.visualstudio.com/)
    VisualStudio Code IDE.

## Utilities ##
- [7zip](http://www.7-zip.org/download.html)
    Compression and archive manager
- [ConEmu](https://conemu.github.io/)
    Tabbed console replacment.
- [Fiddler](http://www.telerik.com/fiddler)
    HTTP debugging proxy.
- [Git for windows](https://git-scm.com/download/win)
    Git distributed version control system.
- [KeePass](http://keepass.info/)
    Password manager
- [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
    SSH and Telnet client.
- [WireShark](https://www.wireshark.org/)
    Network packet analyzer.
- [WinSCP](https://winscp.net/)
    SFTP, FTP, WebDAV and SCP client.
- [WinMerge](http://winmerge.org/)
    diff, merge and comparison tool.
- [VLC](http://www.videolan.org/)
    Media player.
- [SysInternals Handle.exe](https://technet.microsoft.com/en-us/sysinternals/bb896655.aspx)
    Displays information about open handles.
- [Terraform](https://www.terraform.io/downloads.html)
    Infrastructure as code.

## PowerShell ##
- [PsGet](http://psget.net/)
    Search and install PowerShell modules.
- [Posh-Git](http://dahlbyk.github.io/posh-git/)
    PowerShell module which provides Git/PowerShell integration.

# Configuration #

## SSH ##

Posh-Git makes working with git in powershell much easier so install that.

### Option 1. ssh-agent ###

- Use `puttygen` to create your SSH key.
- Save your key (in OpenSSH format) as `~/.ssh/id_rsa` and `~/.ssh/id_rsa.pub`\
  - puttygen produces keys in different format to OpenSSH, use *Conversions* > *Export OpenSSH key* to get the OpenSSH format.
- Add your keys to GitHub, AWS, VisualStudioOnline, etc online.

#### 1.1 If you have multiple different ssh keys ####

Add keys to the `~/.ssh/` directory the filenames in the format `~/.ssh/id_rsa-*keyname*` and `~/.ssh/id_rsa-*keyname*.pub`

For each remote ssh host add the following structure to the `~/.ssh/config` file
```
Host *.example.com
  User exampleuser
  IdentityFile ~/.ssh/id_rsa-*keyname*
```
For AWS IAM, User is the **SSH Key ID**

- You will be prompted for the passphrase for your key each time it's used if you don't add it to the ssh-agent.

  - You could modify your Posh-Git profile (at `%USERPROFILE%\Documents\WindowsPowerShell\Modules\posh-git\profile.example.ps1`)
  to add the keys to the ssh agent so you dont need to keep providing the passphrase.
```
Add-SshKey ~/.ssh/id_rsa-*keyname*
```

### Option 2. KeePass + KeyAgent ###

KeeAgent is a plugin for KeePass that acts a pagent alternative for putty/plink

- Install [KeePass](http://keepass.info/) and [KeeAgent](http://lechnology.com/software/keeagent/).
- Install [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/)
- Use `puttygen` to create SSH key pairs and save them securly somewhere.
- Add your private keys to your KeePass database (and, optionally, delete them off the file system).
- Modify your profile ($profile)
  - Add the following lines to set the GIT_SSH environment var to plink
    ```
    # Use KeeAgent
    $env:GIT_SSH = "plink"
    ```

When you next use git to interact with your remote git the key should be provided by KeePass (which will need to be running)

## Azure ##

Download and install [language-specific SDKs and tools for your platform of choice.](https://azure.microsoft.com/en-gb/downloads/).
For .Net development Azure libraries [come through NuGet](https://www.nuget.org/packages?q=windowsazureofficial) now.
Manage azure resources on the [Azure Portal](https://portal.azure.com/)

## AWS ##

### AWS Command Line Interface ###
With Pyton (and pip) installed, install the AWS Command Line Interface (AWS CLI)
```
pip install awscli
```

### Elastic Beanstalk ###

Install the Elastic Beanstalk Command Line Interface (EB CLI)\
With Python (and pip) installed, install the EB CLI with pip
```
pip install --upgrade --user awsebcli
```
