一、磁盘查看命令

```shell
df -h .
```

查看当前目录所挂载的磁盘使用情况

```shell
du -hd 1 . | sort -hr
```

du 是查看文件夹大小命令

h 参数是指使用human格式，

d 参数是指depth，遍历文件夹深度

1 是指深度为1

sort 表示排序

r   表示逆序排序