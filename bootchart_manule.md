
```
graph LR
系统启动性能分析工具bootchart应用方法
```

工具简介 | 工作周期
---|---
BootChart 是一个用于 linux 启动过程性能分析的开源软件工具 |在内核装载后就开始运行，记录各个程序启动占用的时间、CPU 以及硬盘读写，直到系统启动完成为止
## 应用方法
---
- [ ] 1. - > 下载bootchart源码，地址：https://github.com/xrmx/bootchart.git
- [ ] 2. - > 编译安装: make && sudo make install
- [ ] 3. - > centos7.6平台 编辑/boot/grub2/grub.cfg 文件
- [ ] 4. - > 在linux16 /vmlinuz-3.10.0-957  xxx xxx quiet 之后追加 init=/sbin/bootchartd start
- [ ] 5. - > 针对以上步骤，UOS平台编辑/etc/default/grub文件，设置如下指令：GRUB_CMDLINE_LINUX_DEFAULT="splash quiet init=/sbin/bootchartd start "，然后执行sudo update-grub
- [ ] 6. - > 重启系统
- [ ] 7. - > 登录系统，执行sudo bootchartd stop指令，停止性能监控工具的执行
- [ ] 8. - > 查看/var/log路径下是否生成bootchart.tgz文件
- [ ] 9. - > 如果生成则通过bootchart下的工具生成性能消耗火焰图，执行命令为：./pybootchartgui.py  /var/log/bootchart.tgz  -o  /xxx/xxx/ (/xxx/xxx为生成png图形报表生成目录)
- ---