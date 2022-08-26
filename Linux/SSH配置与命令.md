## 主机指纹
当第一次用 SSH 连接一个服务器主机时，ssh 客户端会有如下提示：
```
$ ssh 192.168.100.123
The authenticity of host '192.168.100.123 (192.168.100.123)' can't be established.
ECDSA key fingerprint is SHA256:QUfCwW6Br5EwwESsulN2TEidBoDNca888RNflZG++bI.
Are you sure you want to continue connecting (yes/no)? yes
```

上面提示主机 `192.168.100.123` 的真实性未确认，当输入 yes 后，会把服务器主机的 host 公钥记录在客户端机的 `.ssh/known_hosts` 中，形如：
```
192.168.100.123 ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBF7Nq0of0/AW+Tphtm1ESs8stGAxxSfQvGYyk0VGPEshHOwU/A6Y4BBIBOjE7egqxkhapxf+BdNmH98DyYhQRps= root@DESKTOP-HP
```

进入服务器主机的 `/etc/ssh` 目录，可以看到一些带有 `host` 名称的公私钥对，例如：
```
ll /etc/ssh/ssh_host_*
-rw------- 1 root root  513 Mar 27 12:09 /etc/ssh/ssh_host_ecdsa_key
-rw-r--r-- 1 root root  182 Mar 27 12:09 /etc/ssh/ssh_host_ecdsa_key.pub
-rw------- 1 root root  411 Mar 27 12:09 /etc/ssh/ssh_host_ed25519_key
-rw-r--r-- 1 root root  102 Mar 27 12:09 /etc/ssh/ssh_host_ed25519_key.pub
-rw------- 1 root root 2.6K Mar 27 12:09 /etc/ssh/ssh_host_rsa_key
-rw-r--r-- 1 root root  574 Mar 27 12:09 /etc/ssh/ssh_host_rsa_key.pub
```

可以在客户机上使用下面命令计算服务器主机指纹：
```
ssh-keyscan -t ECDSA -p 22 192.168.100.123 2>/dev/null | ssh-keygen -E sha256 -lf -
```
详情参考：[验证远程主机SSH指纹](https://www.cnblogs.com/rongfengliang/p/10448225.html)。

## SSH无密码登录
`ssh-keygen` 产生公钥与私钥对，`ssh-copy-id` 将指定的公钥复制到远程机器的 authorized_keys 文件中，ssh-copy-id 能让你有到远程机器的 `home`, `~./ssh` 和 `~/.ssh/authorized_keys`的权利。

具体命令如下：
```bash
# -i：指定公钥文件
ssh-copy-id -i .ssh/id_rsa.pub  用户名字@192.168.x.xxx

# 若没有 ssh-copy-id 命令，可以使用该方法
cat ~/.ssh/id_rsa.pub | ssh 用户名字@192.168.x.xxx "mkdir -p ~/.ssh; cat >> ~/.ssh/authorized_keys"
```
