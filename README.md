# ZTE-MF286D-OpenWrt-24.10.02-by-ilblogdicristiangallo

# OpenWrt MF286D Custom — Version 24.10.2
This customized version of OpenWrt for ZTE MF286D is designed to deliver a complete, ready-to-flash firmware optimized for advanced LTE/5G modem support and post-install automation.

# Key Features
Native USB modem support: built-in drivers for QMI, MBIM, serial, and CDC interfaces

LuCI integration: full support for QMI and ModemManager protocols via web interface

Preconfigured external feeds: IceG repository with GPG key for secure package installation

Includes 4G LTE (4glce) packages: enhanced modem control, signal monitoring, and SMS tools

Bundled packages:

modemmanager, uqmi, usb-modeswitch

kmod-usb-serial-*, kmod-usb-net-*, kmod-mii

luci-app-modemband, luci-app-sms-tool-js, luci-app-3ginfo-lite

luci-proto-qmi, luci-proto-modemmanager

Automated build script: generates sysupgrade.bin and extracts kernel.itb if available

This build is ideal for users who want a plug-and-play firmware for ZTE MF286D, with full modem capabilities, 4G LTE enhancements, and extensibility through custom feeds.

# Install Serial Port

Serial + initramfs:
Place OpenWrt initramfs image for the device on a TFTP in the server's root. This example uses Server IP: 192.168.1.3
Connect serial console (115200,8n1) to X8 connector.
Connect TFTP host to MF286D using an ethernet cable. Don't use the shared WAN/LAN1 port.
Stop u-Boot by pressing ESC, and run u-Boot commands:

<pre>
setenv 

serverip 192.168.1.3
  
setenv ipaddr 192.168.1.72
  
set fdt_high 0x85000000

tftp openwrt-24.10.2-ipq40xx-generic-zte_mf286d-initramfs-zImage_by_ilblogdicristiangallo.itb
</pre>

Terminal Upgrade Process
If you don't have a GUI (LuCI) available, you can alternatively upgrade via the command line.

# sysupgrade
Login as root via SSH on 192.168.1.1, then enter the following commands:
<pre>sysupgrade openwrt-24.10.2-ipq40xx-generic-zte_mf286d-initramfs-zImage_by_ilblogdicristiangallo_sysupgrade.bin</pre>
