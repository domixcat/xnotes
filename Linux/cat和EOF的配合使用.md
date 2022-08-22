## 写入或追加文件
输入格式如下：
```
# 写入(覆盖原来的内容)
cat > 文件名 << EOF
#input something
EOF
```
或者
```
# 追加
cat >> 文件名 << EOF
#input something
EOF
```

用来创建文件，在这之后输入的任何东西，都会写入或追加到文件里，输入完成之后以EOF结尾代表结束。需要注意的是，`EOF`在这里没有特殊的含义，你可以使用FOE或OOO等（当然也不限制在三个字符或大写字符）。
> 注意，不支持在 fish shell 中执行，应该是fish 不兼容这种输入语法。

- 示例1（使用EOF作为输入结束符）：
```
cat > test.txt <<EOF
aaaa
bbbb
cccc
EOF
```
查看文件内容，显示如下：
```
domi@surface-book2:~$ cat test.txt
aaaa
bbbb
cccc
```

- 示例2（使用ab作为输入结束符）：
```
cat > test1.txt <<ab
aaaa1
bbbb2
cccc3
ab
```
查看文件内容，显示如下：
```
domi@surface-book2:~$ cat test1.txt
aaaa1
bbbb2
cccc3
```

## 认知误区
cat不是只能用来看文件，使用man cat命令，查看官方对cat的描述：将[文件]或标准输入(即键盘输入)，输出到标准输出。
```
Concatenate FILE(s) to standard output.

With no FILE, or when FILE is -, read standard input.
```

不加选项参数，直接使用cat，就是直接将标准输入(即键盘输入)输出到标准输出，如下所示：
```
domi@surface-book2:~$ cat
a
a
b
b


^C
```

输入 `a`，cat 会立即输出 `a`。
