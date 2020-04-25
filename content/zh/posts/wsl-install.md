---
title: "WSL与vscode安装"
date: 2020-03-11T15:34:29+08:00
tags: [wsl,vscode,LxRunOffline]
categories: [软件使用,开发环境]
draft: false
---

###  安装WSL

  - #### 启用WSL

    以管理员身份运行 Pow­er­Shell (WIN+X)，输入下面的命令开启 “适用于 Linux 的 Win­dows 子系统” 功能，并重启。

    ```powershell
    Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    ```

  - #### 使用 LxRunOffline 安装 WSL

    下载解压 [LxRunOffline](https://p3terx.com/go/aHR0cHM6Ly9naXRodWIuY29tL0REb1NvbGl0YXJ5L0x4UnVuT2ZmbGluZS9yZWxlYXNlcw==) ，并设置环境变量以便使用`lxrunoffline`命令。

    下载 [WSL 官方离线包](https://p3terx.com/go/aHR0cHM6Ly9kb2NzLm1pY3Jvc29mdC5jb20vZW4tdXMvd2luZG93cy93c2wvaW5zdGFsbC1tYW51YWw=)，解压后可得到名为 `install.tar.gz` 的文件。

    输入以下命令进行安装：

    ```bash
    lxrunoffline i -n <WSL名称> -d <安装路径> -f <安装包路径>install.tar.gz
    ```

    > 加入`-s`参数可在桌面创建快捷方式。
    > 其他lxrunoffline 命令细节,请[参考](https://p3terx.com/archives/manage-wsl-with-lxrunoffline.html)

- #### 修改WSL目录映射关系

  wsl docker安装,需要修改目录映射
  Windows 10 18.03+ 操作方式 `sudo nano /etc/wsl.conf`

  ```ini
  [automount]
  root = /
  options = "metadata"
  ```

  其他低版本采用目录映射

  ```bash
  sudo mkdir /c
  sudo mount --bind /mnt/c /c
  ```

  **安装完成后退出wsl(ctrl+d), 然后`WIN+L`再重新进入,就可以发现`c`盘在根目录了**

- ### 安装vscode

  - 指定插件下载路径

    下载安装vscode,默认插件安装路径在`C:\Users\{USER}\.vscode\extensions`

    可以选择创建软链接的方式安装在其他目录,以减少C盘占用,使用管理员权限打开`CMD`

    ```bash
    # 删除已存在的extensions目录
    rmdir /s/q extensions    
    # 创建软链接
    mklink /D "C:\Users\{USER}\.vscode\extensions" "{指定目录}"
    ```

  - 安装remote-wsl
    
    打开wsl终端窗口，切换到`~`目录，在终端中输入`code-insiders`,执行完毕后
    除了主题等插件外,其他插件会被安装到wsl内.且wsl和windows共享环境变量,
    可以在wsl中直接调用exe程序(需要带上.exe后缀)更多操作请查看[官方文档](https://docs.microsoft.com/en-us/windows/wsl/interop)
  