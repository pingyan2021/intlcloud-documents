<style> table th:first-of-type { width: 200px; } </style>

CDN 支持多项自定义配置，您可以根据自身业务需要进行设置，优化您的 CDN 加速效果。

## 基本配置
| 配置名称                                     | 功能描述                |
| ---------------------------------------- | ------------------- |
| [基本信息](https://intl.cloud.tencent.com/document/product/228/7864) | 支持修改域名所属项目、服务地域和业务类型。 |
| [源站配置](https://intl.cloud.tencent.com/document/product/228/6289) | 域名源站配置：源站基本信息、回源请求协议、回源 Host 和热备源站配置，保障回源。支持境内/境外差异化配置。  |


## 访问控制
| 配置名称                                     | 功能描述                      |
| ---------------------------------------- | ------------------------- |
| [过滤参数配置](https://intl.cloud.tencent.com/document/product/228/35316) | 指定节点是否忽略用户的访问 URL 中"?"之后的参数。 |
| [防盗链配置](https://intl.cloud.tencent.com/document/product/228/6292) | 配置 HTTP referer 黑白名单。支持境内/境外差异化配置。      |
| [IP 黑白名单配置](https://intl.cloud.tencent.com/document/product/228/6298) | 支持设置 IP 黑白名单，进行访问控制。       |
| [IP 访问限频配置](https://intl.cloud.tencent.com/document/product/228/6420) | 支持单 IP 单节点访问限频配置。          |
| [视频拖拽配置](https://intl.cloud.tencent.com/document/product/228/8111) | 支持开启视频拖拽配置。                |
| [鉴权配置](https://intl.cloud.tencent.com/document/product/228/35237) | 配置 URL 鉴权。支持境内/境外差异化配置。 |


## 缓存过期配置
| 配置名称                                     | 功能描述              |
| ---------------------------------------- | ----------------- |
| [缓存过期配置](https://intl.cloud.tencent.com/document/product/228/35317) | 配置指定资源内容的缓存过期时间规则。 |
| [状态码缓存配置](https://intl.cloud.tencent.com/document/product/228/35318) | 403和404状态码缓存时间配置。     |
| [HTTP 头部缓存](https://intl.cloud.tencent.com/document/product/228/35319) | 头部缓存策略配置。          |

## 回源配置
| 配置名称                                     | 功能描述                 |
| ---------------------------------------- | -------------------- |
| [Range 回源配置](https://intl.cloud.tencent.com/document/product/228/7184) | 开启/关闭 Range 分片回源。     |
| [回源跟随301/302配置](https://intl.cloud.tencent.com/document/product/228/7183) | 开启/关闭源站返回301/302时，是否跟随跳转。 |
| [回源超时时间配置](https://intl.cloud.tencent.com/document/product/228/35227) | 配置回源 TCP 连接超时时间和回源加载数据超时时间，保证正常回源。 |


## 高级配置

| 配置名称                                     | 功能描述                             |
| ---------------------------------------- | -------------------------------- |
| [带宽封顶配置](https://intl.cloud.tencent.com/document/product/228/7541) | 对域名设置带宽封顶阈值，超出阈值时关闭 CDN 服务，访问回源站。支持境内/境外差异化配置。 |
| [HTTPS 配置](https://intl.cloud.tencent.com/document/product/228/35212) | 配置 HTTPS 实现安全加速，支持 HTTPS 强制跳转、HTTP2.0 访问和开启/关闭 OCSP 装订。    |
| [SEO 优化配置](https://intl.cloud.tencent.com/document/product/228/35219) | 开启 SEO 优化配置，保证搜索引擎权重稳定性。          |
| [HTTP Header 配置](https://intl.cloud.tencent.com/document/product/228/35320) | 添加 HTTP Header 配置。                |


