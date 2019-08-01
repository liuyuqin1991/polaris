- [相关文章（一些好玩的文章索引）](#相关文章：)
# 相关文章
- [玩转exchange（查找邮件，修改邮件，发送邮件）](https://blog.csdn.net/liuyuqin1991/article/details/86583927)
- [Shell 自动化编译打包](https://blog.csdn.net/liuyuqin1991/article/details/78855230)
- [Linux下rpm及yum安装jdk](https://blog.csdn.net/hg_harvey/article/details/73824084)
- [CentOS 7 安装 Jenkins](https://www.cnblogs.com/stulzq/p/9291237.html)
- [SSL用pem和key文件生成jks文件](https://blog.csdn.net/hfismyangel/article/details/83792992)
```
1、找到openssl的bin目录，找到openssl.exe文件，单击右键以管理员身份运行，打开命令行，输入命令：

pkcs12 -export -out D:\name.pfx -in D:\fullchain.pem -inkey D:\private.key
，按照要求输入两次密码，这时在d盘生成了name.pfx文件。

2、用keytool工具生成jks文件：打开cmd命令工具，进入jdk的bin目录，输入命令：

keytool -importkeystore -srckeystore D:\name.pfx -destkeystore D:\name.jks -srcstoretype PKCS12 -deststoretype JKS
按照要求输入密码，然后在d盘就生成了jks文件。

过程中的输入的密码请牢记。
```