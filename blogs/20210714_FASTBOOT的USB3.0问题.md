# FASTBOOT的USB3.0问题

## 解决方法

1. 换电脑，将数据线插入USB2.0接口
2. 复制以下代码，新建txt文件粘贴进去，然后修改后缀名为bat。右键以管理员权限运行
    ```dos
    @echo off
    reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "osvc" /t REG_BINARY /d "0000" /f
    reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "SkipContainerIdQuery" /t REG_BINARY /d "01000000" /f
    reg add "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100" /v "SkipBOSDescriptorQuery" /t REG_BINARY /d "01000000" /f
    
    pause
    ```

## 还原方法
1. 打开注册表
2. 删除以下三个文件
    ```
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100\osvc
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100\SkipContainerIdQuery
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\usbflags\18D1D00D0100\SkipBOSDescriptorQuery
    ```