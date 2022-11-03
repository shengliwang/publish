
参考： <https://blog.csdn.net/shuangmu9768/article/details/108579207>


这是zip格式的缺陷，zip文件格式中没有字段标志出文件名的编码格式。Windows下生成的zip文件中的编码是GBK/GB2312等，而linux下的默认编码格式为UTF-8，所以才会出现乱码。


### 解决办法一
(使用unzip解压的时候，指定字符集,需要unzip支持，有些unzip命令不支持大O选项，自己可以安装较新的unzip版本）：
```shell
    unzip -O GBK test.zip 推荐使用这个方法
```
### 解决办法二
(借助于p7zip和convmv)
```shell
    yum install p7zip convmv	#centos安装
    apt-get install p7zip convmv    #ubuntu安装
    LANG=C 7za x your-zip-file.zip	#用于解压缩，而LANG=C表示以US-ASCII这样的编码输出文件名，如果没有这个语言设置，它同样会输出乱码，只不过是UTF8格式的乱码(convmv会忽略这样的乱码)。
    convmv -f GBK -t utf8 --notest -r .	#将GBK编码的文件名转化为UTF8编码，-r表示递归访问目录，即对当前目录中所有文件进行转换。
```
### 解决办法三
```shell
    export LANG=zh_CN.UTF-8
    unzip test.zip
```