---
title: "WSL下oh-my-zsh安装"
date: 2020-03-11T16:44:40+08:00
tags: [wsl,oh-my-zsh]
categories: [软件使用,开发环境]
comments: true
draft: false
---
### 安装ZSH

  - 以Ubuntu为例,安装步骤
  ```bash
  # 安装zsh
  sudo apt-get install zsh
  # 安装oh-my-zsh
  sh -c "$(curl https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"

  ```
  - oh-myzsh 其他自定义配置请[参考](https://www.jianshu.com/p/ba782b57ae96)

  - windows文件夹显示问题
    Ubuntu下没有`/etc/DIR_COLORS`,所以需要以下操作
    ```bash
    dircolors -p > ~/.dircolors
    ```
    修改刚生成的文件,推荐vim,可以直接预览颜色
    ```bash    
    vim ~/.dircolors
    ```
    找到如下一行,修改对应颜色
    ```
    OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky
    ```
    例如改为黑色字体红色背景,颜色与背景[参考样式](#style)
    ```
    OTHER_WRITABLE 30;41 # dir that is other-writable (o+w) and not sticky
    ```
    让修改后的文件生效,将下面的代码添加到`~/.zshrc`
    ```
    eval "$(dircolors ~/.dircolors)";
    ```

<a name="style">常见样式参考</a>
  ```
  文字效果  
  00  默认  
  01  加粗 
  04  下划线 
  05  闪烁  
  07  反显  
  08  隐藏  
  文字颜色  
  30 - 黑色
  31 - 红色
  32 - 绿色
  33 - 黄色
  34 - 蓝色
  35 - 洋红色
  36 - 蓝绿色
  37 - 白色
  背景颜色  
  40 - 黑色
  41 - 红色
  42 - 绿色
  43 - 黄色
  44 - 蓝色
  45 - 洋红色
  46 - 蓝绿色
  47 - 白色
 ```