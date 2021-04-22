# wifi模块的使用

## wpa_supplicant.conf配置文件

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
update_config=1

network={
	ssid="HAME"
	proto=WPA2 WPA
	key_mgmt=WPA-PSK
	pairwise=CCMP TKIP
	group=CCMP TKIP
	psk="12345678"
}
```

## 连接wifi

新建脚本文件auto_wifi.sh,添加如下内容

```
echo "insmode 8192 usb wifi"
cd /home/root
insmod 8192cu.ko
ifconfig wlan0 up
wpa_supplicant -Dwext -B -i wlan0 -c /etc/wpa_supplicant.conf
udhcpc -i wlan0 -s /etc/udhcpc.d/50default  &
```
