[官网下载镜像](https://archlinux.org/download/#download-mirrors)
## 文档
[Wiki](https://wiki.archlinux.org/title/Main_page)
[Arch简明指南](https://arch.icekylin.online/)

# 🐧 Arch Linux 安装与故障修复笔记 (Btrfs 压缩方案)

## 一、 磁盘准备与分区

这是最基础的一步。针对之前遇到的 RAID 残留或分区表错误，使用 `g` 建立全新 GPT 分区表是关键。

1. **建立分区表**：
    
    Bash
    
    ```
    fdisk /dev/nvme0n1
    # 输入 g (新建 GPT 分区表)
    # 输入 n (新建 EFI 分区): +512M, 类型设为 1 (EFI System)
    # 输入 n (新建主分区): 剩余全部空间, 默认为 Linux filesystem
    # 输入 w (写入并退出)
    ```
    
2. **格式化分区**：
    
    Bash
    
    ```
    mkfs.fat -F 32 /dev/nvme0n1p1              # 格式化 EFI
    mkfs.btrfs -f -L myArch /dev/nvme0n1p2     # 强制格式化 Btrfs，抹除旧残留
    ```
    

## 二、 Btrfs 子卷管理与挂载

利用 Btrfs 的子卷特性实现系统与数据的逻辑隔离，并开启 `zstd` 压缩以保护 SSD。

1. **创建子卷** [cite: 7-2-2]：
    
    Bash
    
    ```
    mount /dev/nvme0n1p2 /mnt
    btrfs subvolume create /mnt/@
    btrfs subvolume create /mnt/@home
    btrfs subvolume create /mnt/@swap
    umount /mnt
    ```
    
2. **正式挂载 (带压缩参数)** [cite: 7-2-3, 10]：
    
    Bash
    
    ```
    mount -t btrfs -o subvol=/@,compress=zstd /dev/nvme0n1p2 /mnt
    mount --mkdir -t btrfs -o subvol=/@home,compress=zstd /dev/nvme0n1p2 /mnt/home
    mount --mkdir -t btrfs -o subvol=/@swap /dev/nvme0n1p2 /mnt/swap
    mount --mkdir /dev/nvme0n1p1 /mnt/boot
    ```
    

## 三、 基础系统安装

安装时务必带上 `btrfs-progs`，否则系统无法识别自身格式 [cite: 7-2-2]。

Bash

```
pacstrap /mnt base base-devel linux linux-firmware btrfs-progs intel-ucode networkmanager vim sudo
```

## 四、 系统核心配置

此阶段在 `arch-chroot /mnt` 环境内执行 [cite: 7-2-2]。

1. **生成挂载表与 Swap**：
    
    Bash
    
    ```
    genfstab -U /mnt > /mnt/etc/fstab
    btrfs filesystem mkswapfile --size 32G --uuid clear /mnt/swap/swapfile
    swapon /mnt/swap/swapfile
    ```
    
2. **本地化与网络**：
    
    Bash
    
    ```
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
    hwclock --systohc
    # 编辑 /etc/locale.gen 取消 en_US.UTF-8 注释，然后执行:
    locale-gen
    echo "LANG=en_US.UTF-8" > /etc/locale.conf
    echo yanzo > /etc/hostname
    systemctl enable NetworkManager
    passwd  # 设置 Root 密码
    ```
    

## 五、 解决“启动超时”关键补丁 (核心填坑)

**现象**：由于根分区开启了压缩，内核在启动初期若不加载 Btrfs 模块，会导致 `Timed out waiting for device`。

1. **修改内核配置文件**：
    
    Bash
    
    ```
    vim /etc/mkinitcpio.conf
    # 找到 MODULES=()，修改为:
    MODULES=(btrfs)
    ```
    
2. **生成缺失的配置并刷新镜像**：
    
    Bash
    
    ```
    touch /etc/vconsole.conf
    mkinitcpio -P  # 成功后应显示 "Initcpio image generation successful"
    ```
    

## 六、 安装引导程序 (GRUB)

1. **安装包** [cite: 7-2-2]：
    
    Bash
    
    ```
    pacman -S grub efibootmgr
    ```
    
2. **安装并生成配置** [cite: 7-2-2, 11]：
    
    Bash
    
    ```
    grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
    grub-mkconfig -o /boot/grub/grub.cfg
    ```
    

## 七、 安全退出与重启

这是确保数据完整写入硬盘的最后一步 [cite: 7-2-2]。

Bash

```
exit            # 退出 chroot
umount -R /mnt  # 递归卸载，强制 Sync 数据落盘
reboot          # 重启并迅速拔掉 U 盘
```

---

### 💡 进阶建议：

既然你已经成功进入了命令行界面，接下来你可以：

- **装驱动**：执行 `pacman -S sof-firmware` 解决你看到的音频报错。
    
- **建用户**：执行 `useradd -m -G wheel 你的用户名`。
    
- **装桌面**：准备好安装 GNOME 或 KDE Plasma 开启图形化时代。
    

**这份笔记你保存好了吗？如果需要继续安装桌面环境，可以随时告诉我。**