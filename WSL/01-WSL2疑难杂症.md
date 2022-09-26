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

## 安装 mlocate 卡住
Wsl2 的 Ubuntu 系统默认没有安装 mlocate，因此 `locate` 命令无法使用，可以使用 `sudo apt install mlocate` 来安装。

但是在安装完毕后的数据库初始化步骤，安装进度会被卡住，显示如下信息：
```
Initializing plocate database; this may take some time...
```
卡住的原因参见这个[issue](https://github.com/microsoft/WSL/discussions/5967)，即 wsl2 与宿主主机之间的 IO 慢，造成 mlocate 数据库初始化也很慢。

以下是解决方案：在 `/etc/updatedb.conf` 的 `PRUNEPATHS` 字段添加 `/mnt`，即 mlocate 在初始化时排除 `/mnt` 路径。
