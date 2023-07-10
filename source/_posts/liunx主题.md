---
title: Ubuntu更换grub主题
date: 2023-06-24 09:43:23
tags: linux
categories: 学习
cover: /img/f5.png
ai: true
---
# Grub更换主题以及设置Windows 10为第一启动项

Grub（GNU GRand Unified Bootloader）是一款广泛使用的开源引导管理程序，它可以帮助我们在多个操作系统之间进行选择和启动。 Grub的默认外观比较简单，但是我们可以更换主题来改善用户体验。在这篇博客中，我们将学习如何在Grub中更换主题，并将Windows 10设置为第一启动项。

![Grub主题截图](https://img-blog.csdnimg.cn/img_convert/f2388f2af7379bbb23c6a8a254749bf9.png)

## 1. 安装Grub的主题

首先，我们需要下载并安装Grub主题。可以在这里 [GNOME Look](https://www.gnome-look.org/browse/cat/109/) 下载一些美观的主题。

![主题网站](https://i.imgur.com/xhUeS6d.png)

下载后将 `.tar.gz` 的文件解压并将主题文件复制到 `/boot/grub/themes/` 目录下。

## 2. 配置Grub设置文件

接下来，我们需要编辑Grub的设置文件`/etc/default/grub`以启用主题，并将Windows 10设置为默认启动项。

打开`/etc/default/grub`文件，可以看到如下行：

```bash
GRUB_THEME="/path/to/gfxtheme"
```

修改其中的`/path/to/gfxtheme`为相应的主题文件夹名称，例如：

```bash
GRUB_THEME="/boot/grub/themes/MyTheme/theme.txt"
```

要将Windows 10设置为默认启动项，请找到以下行：

```bash
GRUB_DEFAULT=0
```

将`GRUB_DEFAULT`设置为Windows所在的行数。例如，如果Windows是第二个菜单项，则将其设置为`GRUB_DEFAULT=2`。

如果找不到Windows所在的行数，可以使用命令`grep -i "windows" /boot/grub/grub.cfg`搜索。

## 3. 更新Grub

保存修改后，运行以下命令将更改应用于Grub：

```bash
sudo update-grub
```

现在，重新启动计算机，你应该能够看到新的Grub主题并且Windows 10已经成为默认启动项了！

## 结论

在这篇博客中，我们学习了如何更换Grub主题，并将Windows 10设置为默认启动项。这些设置可以使艰难的双引导过程变得更加舒适和美观。

![Grub主题截图2](https://i.imgur.com/4mgT3IN.png)