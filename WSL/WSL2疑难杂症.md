## Landscape 报权限错误
在 windows11 系统下启动 Ubuntu 22.04，会在第一次启动 VM 时报以下错误：
```
/etc/update-motd.d/50-landscape-sysinfo: 17: cannot create /var/lib/landscape/landscape-sysinfo.cache: Permission denied
```

解决方法如下：
```
sudo apt remove landscape-common
sudo apt autoremove
rm ~/.motd_shown
```
参考[stackoverflow该问题](https://askubuntu.com/questions/1414483/landscape-sysinfo-cache-permission-denied-when-i-start-ubuntu-22-04-in-wsl/1414536#1414536?newreg=5cca9ddee1a74c06838ec0b4e733aa07)。
出现的原因在该问题的回答中有解释，大致是因为 WSL 的 Ubuntu 中没有 Systemd 而引起的报错。