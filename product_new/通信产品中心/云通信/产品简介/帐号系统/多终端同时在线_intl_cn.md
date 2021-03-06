
## 概念介绍
### 互踢
默认情况，IM SDK 在同时登录多个终端（如同时登录 PC、Android）时，会进行互踢，只有最后一个登录的设备可以在线，之前登录的都会被踢下线，详细互踢逻辑可以参考以下文档：

- [Android 用户状态变更](https://intl.cloud.tencent.com/document/product/1027/31250)
- [iOS 用户状态变更](https://intl.cloud.tencent.com/document/product/1027/31265)


### 同时在线
云通信 IM 支持在 [控制台](https://console.cloud.tencent.com/avc/list) 修改同时在线策略，通过配置可以做到 PC 端和手机端同时在线，或者 PC、iOS 和 Android 都可以同时在线，开启了同时在线登录不同终端不会互踢（但是两个相同终端，如两个 iOS 端登录仍然会互踢）。


## 功能和限制因素
此功能仅能让多个终端登录，并不保证多端消息的完整性，如果有消息完整性方面的需求，可参阅 [消息存储](https://intl.cloud.tencent.com/document/product/1027/31209)。

