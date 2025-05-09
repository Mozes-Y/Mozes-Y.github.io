+++
date = '2022-07-04T17:31:30+08:00'
draft = false
title = 'powershell美化'
+++

---
title: powershell美化
date: 2022-07-04 17:31:30
category:
      - Tutorial
tags:
      - Tools
---

<!--文章的方法随着时间可能会失效，如果可以，最好能够按照官方给出的最新方式来安装-->

## 下载[Windows terminal](https://github.com/microsoft/terminal)

1. Github上下载自己电脑对应版本，点击上方链接
2. 或者Microsoft store下载Windows terminal

安装完成之后打开terminal

## 下载[powershell core](https://github.com/PowerShell/PowerShell "跨平台的powershell")

**注意**：这是一个跨平台的powershell，与Windows自带的powershell是不同的

下载安装的方法以及各种注意事项见[Microsoft文档](https://docs.microsoft.com/zh-cn/powershell/ "powershell文档")

下载安装完成之后，打开Windows terminal，按下`CTRL+,`打开设置界面，将`"启动"-"默认配置文件"`更改为**powershell**，然后重新启动Windows terminal。

## 下载[posh-git](https://github.com/dahlbyk/posh-git)模块

这是一个支持git状态显示的模块

这是GitHub项目主页中对它的描述

[posh-git is a PowerShell module that integrates Git and PowerShell by providing Git status summary information that can be displayed in the PowerShell prompt.](https://github.com/dahlbyk/posh-git#overview)

如果没有安装过posh-git，则可以在powershell中执行下列命令

```powershell
# (A) You've never installed posh-git from the PowerShell Gallery
PowerShellGet\Install-Module posh-git -Scope CurrentUser -Force
```

如果已经安装过，那么执行下列命令更新

```powershell
# (B) You've already installed a previous version of posh-git from the PowerShell Gallery
PowerShellGet\Update-Module posh-git
```

也可以使用GitHub主页中给出的其它方式来进行下载

然后可以执行

```powershell
Import-Module posh-git
```

注意，这种方法在每次关闭后都会失效，重启之后若想使用，还需要再次执行，因此推荐将其添加到配置文件中

执行下面的命令来配置

```powershell
notepad.exe $PROFILE
```

一般来说，如果没有安装过powershell，notepad会提示文件不存在，并且询问是否建立新文件，点击`是`即可，如果命令行直接提示失败，那么可以执行下面的命令，然后再次使用上面的命令打开配置文件

```powershell
New-Item -Path $PROFILE -Type File -Force
```

再打开配置文件之后，将对应的模块进行配置即可，也就是

```powershell
Import-Module posh-git
```

**注意**：之后的模块配置也是这样，就不再特别提示是否在配置文件中添加，如果不想每次启动都手动配置以便，那么建议添加到配置文件中去

添加成功后重启或者执行下面的命令来使得配置生效

```powershell
. $PROFILE
```

然后进入一个git仓库或者自行初始化一个仓库查看这个配置是否生效，是否已经有git相应的提示信息

## 下载[oh-my-posh](https://ohmyposh.dev/docs/installation/windows)

可以使用Windows下的包管理器winget等下载，也可以使用powershell自带的安装工具下载，可自行在上面的链接中查看，这里我推荐使用powershell的方式来进行手动下载安装，执行下面的命令

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; Invoke-Expression ((New-Object System.Net.WebClient).DownloadString('https://ohmyposh.dev/install.ps1'))
```

如果已经安装，请升级

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; Invoke-Expression ((New-Object System.Net.WebClient).DownloadString('https://ohmyposh.dev/install.ps1'))
```

安装完成之后建议重启terminal来使得一些设置生效

重启之后安装官方的建议字体[Nerd Font](https://www.nerdfonts.com/)中你喜欢的字体进行安装

```powershell
oh-my-posh font install
```

执行上面的命令来进行字体的选择和安装，如果安装失败，也可以进入上面的官网链接中进行下载和手动安装，安装完成之后建议重启，然后进入terminal的设置界面中选择`"配置文件"-"powershell"-"其他设置"-"外观"`(或者也可以在选择配置文件的时候选择默认值，这样就可以将配置应用到terminal可以打开的所有终端中)中选择刚刚安装的字体，同时你也可以进行一些其他的设置，将terminal变为自己喜欢的样子。

## 配置[oh-my-posh](https://ohmyposh.dev/docs)

打开配置文件

```powershell
notepad.exe $PROFILE
```

然后将下面这一行添加到配置文件中，注意，这只是默认配置，后面可以更改为自己喜欢的主题

```powershell
oh-my-posh init pwsh | Invoke-Expression
```

添加成功后重启或者执行下面的命令来使得配置生效

```powershell
. $PROFILE
```

现在应该已经可以启动默认主题，并且正常显示，如果显示不正常，一部分字体无法正常显示的话，应该是字体安装或者选择出现了问题，可以查看字体安装和配置是否成功

当设置成功之后，可以进行主题的替换使用下面的命令查看当前可选的主题

```powershell
Get-PoshThemes
```

执行之后就可以看到当前可选的主题样式，并且每一个主题都将名字以及样式展现了一边，可以选择自己喜欢的主题样式，详细的展示还是可以到上面的官网链接进行查看，选好之后可以打开配置文件，然后将刚刚设置的默认配置修改为下面的形式

```powershell
oh-my-posh init pwsh --config ~/.jandedobbeleer.omp.json | Invoke-Expression
```

这里的`--config`之后的`~/.jandedobbeleer.omp.json`代表默认的主题配置路径以及配置文件，一定要修改为自己的配置文件的路径，如果不知道路径以及格式的话，在执行完上一条命令之后，最后会给出配置文件的本地地址和配置的example，直接复制，然后将主题配置文件修改为你喜欢的主题对应的文件即可，当然，这个配置的选项不仅可以是本地文件，也可以是远程的文件，例如

```powershell
--config 'https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/jandedobbeleer.omp.json'
```

当然，如果有能力的话这些配置都是可以自定义的，建立自己的主题配置文件并修改相应的配置即可

还有更多的细节配置，参考官网给出的文档

## 下载[Terminal-icons](https://github.com/devblackops/Terminal-Icons)

这是一个能在命令行中显示文件的时候给各种文件使用不同图标和颜色的模块，如果喜欢的话可以使用

执行下面的命令进行安装

```powershell
Install-Module -Name Terminal-Icons -Repository PSGallery
```

然后打开配置文件，添加下面的这一行进行配置

```powershell
Import-Module -Name Terminal-Icons
```

---

至此，基本的配置就已经完成，像更加深入和细节的配置，可以按照官方的文档自行配置

**注意**：如果有读者想要使用PSReadLine工具，在powershell 5.1中就已经附带了PSReadLine 2.0.0，之后的版本也附带了更高版本的PSReadLine，如果读者想要使用，无需再次安装，直接在配置文件中启用即可，使用方法请读者自行前往[官方项目](https://github.com/PowerShell/PSReadLine)进行查看。
