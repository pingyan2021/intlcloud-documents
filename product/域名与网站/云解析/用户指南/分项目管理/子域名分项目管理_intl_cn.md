## 概述
腾讯云云解析支持将一级域名下的子域名分配至不同的项目进行管理。例如 qcloud.com 属于默认项目，可以将 cloud.tencent.com 分配至项目 A 进行管理，将 test.qcloud.com 分配至项目 B 进行管理。

需要注意的几点特性是：
- 子域名分项目只针对该域名自身进行分配，不同级的域名之间没有项目归属关系，例如 qcloud.com 属于默认项目，将 cloud.tencent.com 分配至项目 A 后，a.cloud.tencent.com 不会跟随分配至项目 A，a.cloud.tencent.com 仍然是属于默认项目的。
- 拥有子域名权限的协作者，只能针对该子域名自身进行解析，例如 qcloud.com 属于默认项目，将 cloud.tencent.com 分配至项目 A 后，协作者仅仅可以添加例如 `www.qlcoud.com` > A 记录 > 8.8.8.8 这样的解析记录（主机记录只能是 www），不能添加 qcloud.com、a.cloud.tencent.com 域名的解析记录（主机记录不能是 @、a.www）。
- 域名在项目间进行分配和移动，不会影响现有解析。

## 操作指南
### 分配已添加过解析的子域名
1. 方式一
在域名的记录管理页，勾选解析记录分配项目，这样对应的子域名将归属指定的项目进行管理，例如图中勾选 `www.qcloud-example.com` 进行项目分配。
![](//mc.qcloudimg.com/static/img/60ca6fd590a8c607bfd47df84a362270/image.png)
2. 方式二
勾选一级域名，单击【批量操作】>【分配其子域名至项目】，弹窗中可输入子域名进行分配。
![](//mc.qcloudimg.com/static/img/73e344ba533817ca84623d23158dc359/image.png)
![](//mc.qcloudimg.com/static/img/8dc6737c5e6508cf161d19f2776b1f59/image.png)
例如输入 www，则加载出主机记录 www 对应的解析记录，子域名分配项目后，解析记录不会受影响，跟随子域名到对应的项目。
![](//mc.qcloudimg.com/static/img/3ec9f9375d56f8e73241c697b4efcb48/image.png)
### 分配未添加过解析的子域名
未添加过解析的子域名同样也可以进行分配，例如输入 test，`test.qcloud-example.com `并没有添加过解析，仍然可以分配项目进行管理。
![](//mc.qcloudimg.com/static/img/a5f791477e5bd07ef4be8ce80f80bfb8/image.png)
### 项目权限
在协议子域名列表，项目 123 的协作者可以对项目 123 下的子域名进行解析操作，
![](//mc.qcloudimg.com/static/img/da641d70cf664895938a8e0e302c4aab/image.png)
但是仅能添加【协作子域名】列表中的子域名自身的解析，例如图中只能添加 www、test 的解析记录。
![](//mc.qcloudimg.com/static/img/2118da62aa76deeaf1d7b1d9ed395163/image.png)
同样，项目 123 的协作者也可以对属于项目 123 的子域名进行项目分配，如果该协作者同时有项目 456 的权限，则可以移动到项目 456。
![](//mc.qcloudimg.com/static/img/7071d7046f4aefb376545d77d3cbe6bd/image.png)
全局协作者可以对一级域名的解析记录进行项目筛选，查看不同项目中添加了哪些解析。
![](//mc.qcloudimg.com/static/img/cd42f9711c42ea0884873a6818aa1e69/image.png)