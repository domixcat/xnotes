## Git 的配置文件在哪里
在 Windows 系统下，Git 的全局配置文件路径为 `%userprofile%/.gitconfig`。在 Linux 系统下，路径为 `$HOME/.gitconfig`。

每个 git 仓库也可以有自己的配置，配置文件路径在项目根目录的 `.git/config` 中。


## 定制git log
输入以下命令：
```
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative"
```

显示效果如下：
```
*   4c9c2ac - Merge branch 'lvzixun-self_skynet' (3 years, 5 months ago) <Cloud Wu>
|\
| * bfbbe91 - turn off ltls by default (3 years, 5 months ago) <Cloud Wu>
| *   eda9f77 - Merge branch 'self_skynet' of https://github.com/lvzixun/skynet into lvzixun-self_skynet (3 years, 5 months ago) <Cloud Wu>
| |\
| | * 7746193 - add https client and server support by bios (3 years, 5 months ago) <zixun>
* | |   7cb4bbb - Merge branch 'cluster' (3 years, 5 months ago) <Cloud Wu>
|\ \ \
| * | | 1c3b563 - add wait queue (3 years, 5 months ago) <Cloud Wu>
| * | | 000fa2b - multi cluster sender (3 years, 5 months ago) <Cloud Wu>
* | | |   2c247b5 - Merge branch 'sharedk' (3 years, 5 months ago) <Cloud Wu>
|\ \ \ \
| * | | | 3f38a71 - Shared K (3 years, 5 months ago) <Cloud Wu>
| |/ / /
* | / / ea1affd - fix #962 (3 years, 5 months ago) <Cloud Wu>
| |/ /
|/| |
* | | 9ffdf2d - Update skynet_daemon.c (3 years, 5 months ago) <Dalton>
|/ /
* | 1d4308f - Fix memory leak, See #952 (3 years, 6 months ago) <Cloud Wu>
* | 48e5c36 - volatile for signal, see #950 (3 years, 6 months ago) <Cloud Wu>
|/
* 1422cae - Consider __pairs, see #942 (3 years, 6 months ago) <Cloud Wu>
* 9e16b04 - dns reInit bug (3 years, 7 months ago) <Naix>
* 0fbbd5f - type can be DATA (3 years, 7 months ago) <Cloud Wu>
* 6eb9b64 - remove mysqlaux.c (3 years, 7 months ago) <Cloud Wu>
* d71c8f8 - remove new_tab (3 years, 7 months ago) <Cloud Wu>
```

## 指定合并规则


`git config merge.ours.driver true`