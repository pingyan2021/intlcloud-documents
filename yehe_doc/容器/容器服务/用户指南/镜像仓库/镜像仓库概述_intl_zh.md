## 镜像仓库概述
镜像仓库用于存放 Docker 镜像，Docker 镜像可用于部署容器服务，每个镜像有特定的唯一标识（镜像的 Registry 地址+镜像名称+镜像 Tag）。

## 镜像类型
目前镜像支持 Docker Hub 官方镜像和用户私有镜像。

## 镜像生命周期

镜像生命周期主要包含镜像版本的生成、上传和删除。为了更方便的管理全局镜像，腾讯云容器服务 TKE 引入以下镜像生命周期管理：
- 支持开启全局镜像生命周期管理。启用后，所配置的全局规则将应用于主账号下所有镜像。
- 支持对指定镜像仓库独立配置镜像版本自动清理策略，该策略优先级高于全局配置。

您可参考 镜像生命周期管理 设置镜像仓库下镜像的生命周期。


## 使用帮助
- [镜像仓库基本操作](https://intl.cloud.tencent.com/document/product/457/9117)
- 镜像生命周期管理
- [如何构建 docker 镜像](https://intl.cloud.tencent.com/document/product/457/9115)
- [如何搭建私有镜像仓库](https://intl.cloud.tencent.com/document/product/457/9114)
- [使用 DockerHub 加速器](https://intl.cloud.tencent.com/document/product/457/9113)
