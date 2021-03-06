### 通过web终端登录到容器(推荐)
1.单击进入[容器服务控制台页面](https://console.cloud.tencent.com/tke2)。
2.选择容器所属节点，单击进入Pod管理详情页，查看实例列表，选择容器并登录远程终端。
3.更多远程终端常见问题单击[查看详情](https://intl.cloud.tencent.com/document/product/457/31426)

![Alt text](https://main.qcloudimg.com/raw/5950f1840fb625fc1797b83247952560.png)

### 通过容器所在节点登录到容器
1.获取容器所在节点IP地址，容器ID。
![Alt text](https://main.qcloudimg.com/raw/29132c94a222bf904210d6592957f636.png)

2.登录到节点，详情查看[登录到云主机](https://intl.cloud.tencent.com/doc/product/213/5436)。

3.通过docker ps命令查看需登录的容器。
```shell
[root@VM_88_88_centos ~]# docker ps | grep 75b3b15af61a  
75b3b15af61a       nginx:latest                                 "nginx -g 'daemon off"   About a minute ago   Up About a minute                       k8s_worid.e8b44cc_worid-24bn2_default_81a59654-aa14-11e6-8a18-52540093c40b_42c0b746
```
4.通过docker exec命令登录到容器。
```shell
[root@VM_0_60_centos ~]# docker ps | grep 75b3b15af61a
75b3b15af61a        nginx:latest                                 "nginx -g 'daemon off"   2 minutes ago       Up 2 minutes                            k8s_worid.e8b44cc_worid-24bn2_default_81a59654-aa14-11e6-8a18-52540093c40b_6b389dd2
[root@VM_0_60_centos ~]# docker exec -it 75b3b15af61a /bin/bash
root@worid-24bn2:/# ls
bin  boot  dev	etc  home  lib	lib64  media  mnt  opt	proc  root  run  sbin  srv  sys  tmp  usr  var
```

### 容器已安装SSH服务端，通过SSH登录到容器
1.获取容器IP地址。
![Alt text](https://main.qcloudimg.com/raw/b66ad2e4d243215ccf24a0bad3ac0e71.png)

2.登录集群内任意节点,详情查看[登录到云主机](https://intl.cloud.tencent.com/doc/product/213/5436)。

3.通过SSH登录到容器。



