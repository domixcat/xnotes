编辑 `.bashrc` 文件，添加以下内如：

```bash
# highlight man page
export MANPAGER="less -isgN"
export LESS_TERMCAP_mb=$'\E[01;31m'         # begin blinking
export LESS_TERMCAP_md=$'\E[01;31m'         # begin bold
export LESS_TERMCAP_me=$'\E[0m'             # end mode
export LESS_TERMCAP_se=$'\E[0m'             # end standout-mode
export LESS_TERMCAP_so=$'\E[01;44;33m'      # begin standout-mode - info box
export LESS_TERMCAP_ue=$'\E[0m'             # end underline
export LESS_TERMCAP_us=$'\E[01;32m'         # begin underline
```

保存退出后，执行 `source .bashrc` 生效。
