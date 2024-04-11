此项目源于ImmortalWrt，源代码来自
https://github.com/hanwckf/immortalwrt-mt798x.git
## 设置
默认IP: http://192.168.1.7 or http://immortalwrt.lan 

用户名: root
密码: none

## 相关介绍
- https://cmi.hanwckf.top/p/immortalwrt-mt798x/

### 要求
- 要使用这个项目进行构建，首选ubuntu 20.04 lts。你需要使用amd64架构上的代码，至少有4gb的内存和25 gb的可用磁盘空间。确保互联网是可访问的。

- 安装依赖

  1.使用普通用户身份
  2.安装依赖
  方式一：
  ```bash
  sudo apt update -y
  sudo apt full-upgrade -y
  sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
  bzip2 ccache clang clangd cmake cpio curl device-tree-compiler ecj fastjar flex gawk gettext gcc-multilib \
  g++-multilib git gperf haveged help2man intltool lib32gcc-s1 libc6-dev-i386 libelf-dev libglib2.0-dev \
  libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses5-dev libncursesw5 libncursesw5-dev libreadline-dev \
  libssl-dev libtool lld lldb lrzsz mkisofs msmtp nano ninja-build p7zip p7zip-full patch pkgconf python2.7 \
  python3 python3-pip python3-ply python-docutils qemu-utils re2c rsync scons squashfs-tools subversion swig \
  texinfo uglifyjs upx-ucl unzip vim wget xmlto xxd zlib1g-dev
  ```
  方式二：
  ```bash
  sudo bash -c 'bash <(curl -s https://build-scripts.immortalwrt.eu.org/init_build_environment.sh)'
  ```

  注意:
  - 使用非root用户
  - 路径或者文件名不能有空格或者非ascii字符
  - 有问题参照以下文档
    https://openwrt.org/docs/guide-developer/build-system/install-buildsystem

### 编译
1. 拉取源码
  ```bash
  git clone --depth=1 https://github.com/reflander/flawrt.git
  ```
2. 转到文件夹
  ```bash
  cd flawrt
  ```
3. 更新安装包
  ```bash
  ./scripts/feeds update -a
  ```

4. 安装包
  ```bash
  ./scripts/feeds install -a
  ```

5. 从`defconfig` 文件夹复制配置文件并重命名为 `.config`
    
    ```
    # MT7981
    cp -f defconfig/mt7981-ax3000.config .config

    # MT7986
    cp -f defconfig/mt7986-ax6000.config .config
    
    # MT7986 256M Low Memory
    cp -f defconfig/mt7986-ax6000-256m.config .config
    
    # x86
    cp -f defconfig/x86.config .config
    
    ``` 
     
  6. 选择您偏好的工具链、目标系统和固件包的配置
  ```bash
  make menuconfig
  ```
  7. 构建您的固件。这将下载所有源代码，构建交叉编译工具链，然后为您的目标系统交叉编译 GNU/Linux 内核和所有选择的应用程序。
  ```bash
   make V=s -j$(nproc)
  ```
  

## 相关存储库

主存储库使用多个子存储库来管理不同类别的软件包。所有软件包均通过 ImmortalWrt 软件包管理器 opkg 安装。如果您想开发 Web 界面或将软件包移植到 ImmortalWrt，请在下面找到相应的存储库。

- [LuCI Web 界面](https://github.com/immortalwrt/luci)：现代化和模块化的界面，可通过 Web 浏览器控制设备。
- [ImmortalWrt 软件包](https://github.com/immortalwrt/packages)：移植软件包的社区存储库。
- [OpenWrt 路由](https://github.com/openwrt/routing)：专注于（网状）路由的软件包。

## 支持信息
有关受支持设备的列表，请参阅[OpenWrt 硬件数据库](https://openwrt.org/supported_devices)
  ### Documentation
  - [快速入门指南](https://openwrt.org/docs/guide-quick-start/start)
  - [用户指南](https://openwrt.org/docs/guide-user/start)
  - [开发者文档](https://openwrt.org/docs/guide-developer/start)
  - [技术参考](https://openwrt.org/docs/techref/start)

  ### 支持社区
  - 支持聊天: group [@ctcgfw_openwrt_discuss](https://t.me/ctcgfw_openwrt_discuss) on [Telegram](https://telegram.org/).
  - 支持聊天: group [#immortalwrt](https://matrix.to/#/#immortalwrt:matrix.org) on [Matrix](https://matrix.org/).

## 许可证
ImmortalWrt is licensed under [GPL-2.0-only](https://spdx.org/licenses/GPL-2.0-only.html).

## 致谢
<table>
  <tr>
    <td><a href="https://dlercloud.com/"><img src="https://user-images.githubusercontent.com/22235437/111103249-f9ec6e00-8588-11eb-9bfc-67cc55574555.png" width="183" height="52" border="0" alt="Dler Cloud"></a></td>
    <td><a href="https://www.jetbrains.com/"><img src="https://resources.jetbrains.com/storage/products/company/brand/logos/jb_square.png" width="120" height="120" border="0" alt="JetBrains Black Box Logo logo"></a></td>
    <td><a href="https://sourceforge.net/"><img src="https://sourceforge.net/sflogo.php?type=17&group_id=3663829" alt="SourceForge" width=200></a></td>
  </tr>
</table>
