## 查看当前时区
```
date -R
#输出： Fri, 26 Aug 2022 18:43:35 +0800
# 后面的 +0800 表示时区

# 或者
date +"%z"
```

## 修改系统时区
```bash
# -f 强制修改
sudo ln -s -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

## 修改用户时区
Linux 用户一个多用户系统，每个用户都可以配置自己所需的时区，可以在用户目录的 `.bashrc` 中新增一个 TZ 环境变量：
```
export TZ='Asia/Shanghai'
```
然后重新登陆或执行 `source .bashrc` 生效。


## timedatectl 设置时区
```
sudo timedatectl set-timezone 'Asia/Shanghai'
```
