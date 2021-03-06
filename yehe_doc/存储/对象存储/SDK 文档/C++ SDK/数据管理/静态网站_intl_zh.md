

## 简介

本文档提供关于静态网站的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名           | 操作描述                 |
| ------------------------------------------------------------ | ---------------- | ------------------------ |
| [PUT Bucket website](https://intl.cloud.tencent.com/document/product/436/30617) | 设置静态网站     | 设置存储桶的静态网站配置 |
| [GET Bucket website](https://intl.cloud.tencent.com/document/product/436/30616) | 查询静态网站配置 | 查询存储桶的静态网站配置 |
| [DELETE Bucket website](https://intl.cloud.tencent.com/document/product/436/30629) | 删除静态网站配置 | 删除存储桶的静态网站配置 |

## 设置静态网站

#### 功能说明

PUT Bucket website 用于为存储桶配置静态网站。

#### 方法原型

```cpp
CosResult CosAPI::PutBucketWebsite(const PutBucketWebsiteReq& request,PutBucketWebsiteResp* response);
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::PutBucketWebsiteReq req(bucket_name);
qcloud_cos::PutBucketWebsiteResp resp;

req.SetSuffix("index.xml"); //必选项
req.SetProtocol("https");
req.SetKey("Error.html");

//设置重定向规则，最多设置100条 

// 设置第一条规则
qcloud_cos::RoutingRule routerule1;
qcloud_cos::Condition temp_condtion1;
temp_condtion1.SetHttpErrorCodeReturnedEquals(404);//需要设置，默认404
routerule1.SetCondition(temp_condtion1);
qcloud_cos::Redirect temp_redirect1;
temp_redirect1.SetProtocol("https");
temp_redirect1.SetReplaceKeyWith("404.htmp");
routerule1.SetRedirect(temp_redirect1);

// 设置第二条规则
qcloud_cos::RoutingRule routerule2;
qcloud_cos::Condition temp_condtion2;
temp_condtion2.SetHttpErrorCodeReturnedEquals(403);//需要设置，默认404
routerule2.SetCondition(temp_condtion2);
qcloud_cos::Redirect temp_redirect2;
temp_redirect2.SetProtocol("https");
temp_redirect2.SetReplaceKeyWith("403.htmp");
routerule2.SetRedirect(temp_redirect2);

// 设置第三条规则
qcloud_cos::RoutingRule routerule3;
qcloud_cos::Condition temp_condtion3;
temp_condtion3.SetKeyPrefixEquals("img/");
temp_condtion3.SetHttpErrorCodeReturnedEquals(402);
routerule3.SetCondition(temp_condtion3);
qcloud_cos::Redirect temp_redirect3;
temp_redirect3.SetProtocol("https");
temp_redirect3.SetReplaceKeyWith("401.htmp");
routerule3.SetRedirect(temp_redirect3);

// 设置第四条规则
qcloud_cos::RoutingRule routerule4;
qcloud_cos::Condition temp_condtion4;
temp_condtion4.SetKeyPrefixEquals("img1/");
routerule4.SetCondition(temp_condtion4);
qcloud_cos::Redirect temp_redirect4;
temp_redirect4.SetProtocol("https");
temp_redirect4.SetReplaceKeyPrefixWith("402.htmp");
routerule4.SetRedirect(temp_redirect4);

req.AddRoutingRule(routerule1);
req.AddRoutingRule(routerule2);
req.AddRoutingRule(routerule3);
req.AddRoutingRule(routerule4);

qcloud_cos::CosResult result = cos.PutBucketWebsite(req, &resp);

if (result.IsSucc()) {
	// 请求成功
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

#### 参数说明

| 参数 | 参数描述                  | 类型                | 是否必填  |
| ---- | --------------------------| --------------------| ------|
| req  | PutBucketWebsite 操作的请求| PutBucketWebsiteReq | 是    |
| resp | PutBucketWebsite 操作的响应| PutBucketWebsiteResp| 是    |


## 查询静态网站配置

#### 功能说明

GET Bucket website 用于查询与存储桶关联的静态网站配置信息。

#### 方法原型

```cpp
CosResult CosAPI::GetBucketWebsite(const GetBucketWebsiteReq& request, GetBucketWebsiteResp* response);
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::GetBucketWebsiteReq req(bucket_name);
qcloud_cos::GetBucketWebsiteResp resp;

qcloud_cos::CosResult result = cos.GetBucketWebsite(req, &resp);

if (result.IsSucc()) {
	// 请求成功，通过 resp 获取静态网站配置
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

#### 参数说明

| 参数 | 参数描述                  | 类型                | 是否必填  |
| ---- | --------------------------| --------------------| ------|
| req  | GetBucketWebsite 操作的请求| GetBucketWebsiteReq | 是    |
| resp | GetBucketWebsite 操作的响应| GetBucketWebsiteResp| 是    |


GetBucketWebsiteResp 提供如下方法获取静态网站配置：
```cpp
std::vector<RoutingRule> GetRoutingRules() const;
```

RoutingRule 的定义可以参考 SDK 头文件。


## 删除静态网站配置

#### 功能说明

DELETE Bucket website 用于删除存储桶中的静态网站配置。

#### 方法原型

```java
CosResult CosAPI::DeleteBucketWebsite(const DeleteBucketWebsiteReq& request, DeleteBucketWebsiteResp* response);
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::DeleteBucketWebsiteReq req(bucket_name);
qcloud_cos::DeleteBucketWebsiteResp resp;

qcloud_cos::CosResult result = cos.DeleteBucketWebsite(req, &resp);

if (result.IsSucc()) {
	// 请求成功
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

#### 参数说明

| 参数 | 参数描述                     | 类型                   | 是否必填  |
| ---- | -----------------------------| -----------------------| ------|
| req  | DeleteBucketWebsite 操作的请求| DeleteBucketWebsiteReq | 是    |
| resp | DeleteBucketWebsite 操作的响应| DeleteBucketWebsiteResp| 是    |

