## 用ssh免密码登录服务器

#### Root用户
> 1.客户机生成私钥公钥


> 2.用scp命令将**客户机公钥**拷贝至服务器 或者 直接复制到.ssh/authorized_keys文件下（没有则新建）

```
scp ~/.ssh/id_rsa.pub root@yourhost:.ssh/copy_key

cat copy_key >> authorized_keys
```

>3.拷贝完成后把authorized_keys的权限修改为600则可。



#### 普通用户

普通用户在完成上述步骤后，（即对应root下的/home/username/目录）
需要一些权限的配置。

>1.修改用户主目录的权限, /home/username目录权限为755


>2..ssh的权限设置为700， authorized_keys的权限设置为600就够了，属主要是登陆用户自己（root是不行的），组无所谓

完成以上操作后，就能免密码登录了。



#### MAC Shell 快捷命令

虽然能免密码登录能够一定程度的方便我们，但是每次输入用户名和主机名还是比较麻烦的。
mac用户可以考虑使用alias命令写个简单的命令。
不过我更推荐另一种做法：

>在.ssh文件夹下新建config文件，在其中添加如下内容：

```shell
Host returngirl
    HostName yourhost.cn
    Port 22
    User username
```
然后每次登陆只需要：
```shell
ssh returngirl
```
即可。
