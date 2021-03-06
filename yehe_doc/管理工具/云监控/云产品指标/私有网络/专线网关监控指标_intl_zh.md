## 命名空间


Namespace=QCE/DCG


## 监控指标

| 指标英文名   | 指标中文名 | 单位  | 维度                   |
| ------------ | ---------- | ----- | ---------------------- |
| Outbandwidth | 外网出带宽 | Mbps  | directConnectGatewayId |
| Inbandwidth  | 外网入带宽 | Mbps  | directConnectGatewayId |
| Outpkg       | 出包量     | 个/秒 | directConnectGatewayId |
| Inpkg        | 入包量     | 个/秒 | directConnectGatewayId |

>每个指标对应的统计粒度（Period）可取值不一定相同，可通过 [DescribeBaseMetrics](https://intl.cloud.tencent.com/document/product/248/33882) 接口获取每个指标支持的统计粒度信息。

## 各维度对应参数总览

| 参数名称               | 维度名称             | 维度解释          | 格式                            |
| ------------------ | ---------------- | ------------- | ----------------------------- |
| Instances.N.Dimensions.0.Name  | directConnectGatewayId               | 专线网关 ID 的维度名称 | 输入 String 类型维度名称：directConnectGatewayId       |
| Instances.N.Dimensions.0.Value | directConnectGatewayId               | 专线网关具体 ID  | 输入专线网关具体 ID：dcg-4d545d |

## 入参说明

查询私有网络专线网关监控数据，入参取值如下：
&Namespace=QCE/DCG
&Instances.N.Dimensions.0.Name=directConnectGatewayId
&Instances.N.Dimensions.0.Value 为专线网关 ID
