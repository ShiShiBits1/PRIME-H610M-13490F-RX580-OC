# 💻 黑苹果OpenCore EFI配置方案

## 📋 硬件配置

- **CPU**: 13th Gen Intel(R) Core(TM) i5-13490F (2.50 GHz)
- **主板**: PRIME H610M-E D4
- **显卡**: AMD RX580 8G
- **声卡**: ALC897

## ✨ EFI特点

- 基于OpenCore引导程序
- 支持macOS Ventura/Sonoma
- 完善的ACPI补丁
- 优化的USB端口映射
- 显卡驱动完美支持
- 声卡正常工作
- 以太网正常驱动
- 睡眠唤醒功能

## 📁 EFI目录结构

```
EFI/
├── APPLE/
├── BOOT/
│   └── BOOTx64.efi
└── OC/
    ├── ACPI/
    │   ├── SSDT-AWAC-DISABLE.aml
    │   ├── SSDT-Alder-Lake.aml
    │   ├── SSDT-EC-USBX.aml
    │   ├── SSDT-GPRW.aml
    │   └── SSDT-PLUG-ALT.aml
    ├── Drivers/
    │   ├── HfsPlus.efi
    │   ├── OpenCanopy.efi
    │   ├── OpenRuntime.efi
    │   └── ResetNvramEntry.efi
    ├── Kexts/
    │   ├── AppleALC.kext
    │   ├── CpuTopologyRebuild.kext
    │   ├── Lilu.kext
    │   ├── RealtekRTL8111.kext
    │   ├── RestrictEvents.kext
    │   ├── SMCProcessor.kext
    │   ├── SMCSuperIO.kext
    │   ├── USBPorts.kext
    │   ├── VirtualSMC.kext
    │   ├── WhateverGreen.kext
    ├── OpenCore.efi
    ├── Resources/
    ├── Tools/
    ├── config.plist
    └── config_自行添加3码.plist
```

## 🚀 安装指南

1. **准备工作**
   - 下载macOS安装镜像
   - 使用[BalenaEtcher](https://www.balena.io/etcher/)制作启动U盘
   - 备份你的重要数据

2. **配置BIOS**
   - 关闭安全启动
   - 禁用CSM
   - 设置SATA模式为AHCI
   - 禁用VT-d
   - 启用XMP内存配置文件

3. **安装EFI**
   - 将此EFI文件夹复制到U盘的EFI分区
   - 替换U盘中原有的EFI文件夹

4. **安装macOS**
   - 从U盘启动
   - 选择"Install macOS Ventura/Sonoma"
   - 按照安装向导完成安装

5. **后期配置**
   - 安装完成后，将EFI文件夹复制到硬盘的EFI分区
   - 生成并添加你的三码(Serial, MLB, UUID)
   - 重启电脑并享受黑苹果系统

## 🔧 故障排除

- **显卡问题**: 确保WhateverGreen.kext已加载，检查config.plist中的显卡参数
- **声卡问题**: 确认AppleALC.kext已安装，layout-id设置正确
- **USB问题**: 使用USBToolBox重新映射USB端口
- **睡眠问题**: 检查ACPI补丁是否正确，特别是SSDT-GPRW.aml
- **启动问题**: 重置NVRAM，检查OpenCore版本与macOS版本兼容性

## 🙏 感谢

- [OpenCore官方文档](https://dortania.github.io/OpenCore-Post-Install/)
- [Acidanthera](https://github.com/acidanthera)提供的驱动和工具
- [愿景论坛](https://bbs.pcbeta.com/forum.php)的帮助和支持

## 📝 注意事项

- 本EFI配置仅适用于上述硬件配置
- 安装前请确保已备份所有重要数据
- 黑苹果系统可能存在稳定性问题，请谨慎使用
- 请自行生成三码，不要使用他人分享的三码
- 本配置仅供学习和研究使用，请勿用于商业用途

希望这个EFI配置能帮助你顺利安装和使用黑苹果系统！如果遇到问题，请查阅上面的故障排除部分或寻求社区帮助。

祝你黑苹果之旅愉快！ 🍎

        