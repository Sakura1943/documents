# Arch Linux

> 收藏一些`Arch Linux`使用过程中遇到的问题以及解决方法，获得使用小技巧以及工具
---
# 工具
- ## `bottom`
  `rust`编写的系统状态监视器， 类似于`htop`的功能
  - ### 安装
    ```bash
    cargo install bottom
    ```
    或者
    ```bash
    pacman -Sy bottom
    ```
- ## `gst-plugin-pipewire`
`Gnome`桌面的视频录制功能的插件
  - ### 安装
    ```bash
    pacman -Sy gst-plugin-pipewire
    ```

- ## `yrm`
  `yrm` 或 `npm` 仓库操作工具
  - ### 安装
    ```bash
    npm install -g yrm
    ```

- ## `crm`
  `crates`仓库管理以及`cargo`镜像源管理工具
  - ### 安装
    ```bash
    cargo install crm
    ```