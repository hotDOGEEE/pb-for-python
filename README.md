# pb-for-python

# win10 protobuf-python的安装过程记录

现在网上的资料总是很杂的，再加上各种爬虫，不注明的转载侵权，信息有效性已经很低了。

随着新版本的协议压测内容迭代，我进行了一次python3.7到3.10的迁移操作。

试图用requirements的形式对新环境直接进行迁移，然而我忘记了protobuf的安装过程是复杂的。

于是乎又忘了怎么操作的我，这里进行一下备注，以便下次不走弯路。



## 所需材料

https://github.com/protocolbuffers/protobuf/releases

官方已于10/2021发布了支持python3.10的版本（v3.19.0）

强烈建议后续大家采用python3.10版本来进行协议相关的内容，主要是其中有关模式匹配的语法非常适合协议测试下的场景使用。

原则上版本越新越好。

![](https://i.bmp.ovh/imgs/2021/11/b548dc79dbc348d6.png)

## 安装过程

1. 在该地址下下载同版本的两个文件，分别解压。
2. 将win64中的exe文件配置于环境变量（有老版本的记得删除老版本配置）。
3. 配置好后protoc --version查看版本，有返回则成功。
4. python切换到对应python环境后（针对使用虚拟环境用户）进入protobuf-python解压文件夹的python文件夹下面，命令行依次输入: python setup.py build>python setup.py test>python setup.py install 最后提示finished说明安装成功

## 如何使用

已有proto文件的情况下,使用protoc --python_out=./ ./protofile.proto即可生成。

于python中使用，直接导入生成的.py文件。各种协议就是你的对象，想引用谁就引用谁。

先填入对应对象的各个对象值，用pb的方法进行序列化，就可以进行通信了。这是一个对称的协议，反序列化逆向进行没有问题。

