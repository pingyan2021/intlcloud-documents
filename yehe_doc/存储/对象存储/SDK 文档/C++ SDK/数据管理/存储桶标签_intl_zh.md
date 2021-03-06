## 简介

本文档提供关于存储桶标签的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名         | 操作描述                         |
| ------------------------------------------------------------ | -------------- | -------------------------------- |
| [PUT Bucket tagging](https://intl.cloud.tencent.com/document/product/436/8281) | 设置存储桶标签 | 为已存在的存储桶设置标签         |
| [GET Bucket tagging](https://intl.cloud.tencent.com/document/product/436/8277) | 查询存储桶标签 | 查询指定存储桶下已有的存储桶标签 |
| [DELETE Bucket tagging](https://intl.cloud.tencent.com/document/product/436/8286) | 删除存储桶标签 | 删除指定的存储桶标签             |

## 设置存储桶标签

#### 功能说明

PUT Bucket tagging 用于为已存在的存储桶设置标签。

#### 方法原型

```cpp
CosResult PutBucketTagging(const PutBucketTaggingReq& request, PutBucketTaggingResp* response);
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::PutBucketTaggingReq req(bucket_name);
qcloud_cos::PutBucketTaggingResp resp;

std::vector<Tag> tagset;
Tag tag1;
tag1.SetKey("age");
tag1.SetValue("19");

Tag tag2;
tag2.SetKey("name");
tag2.SetValue("xiaoming");
tagset.push_back(tag1);
tagset.push_back(tag2);
req.SetTagSet(tagset);

qcloud_cos::CosResult result = cos.PutBucketTagging(req, &resp);

if (result.IsSucc()) {
    // 请求成功
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```


#### 参数说明

| 参数 | 参数描述                   | 类型                | 是否必填  |
| ---- | ---------------------------| --------------------| ------|
| req  | PutBucketTagging 操作的请求 | PutBucketTaggingReq | 是    |
| resp | PutBucketTagging 操作的响应 | PutBucketTaggingResp| 是    |



PutBucketTaggingReq 提供以下方法：

```
void SetTagSet(std::vector<Tag>& tagset)   // 设置 tagging
```

Tag 提供以下方法：

```cpp
class Tag {
    void SetKey(const std::string key);  // 设置 key
    void SetValue(const std::string value);  // 设置 value
```


## 查询存储桶标签

#### 功能说明

GET Bucket tagging 用于查询指定存储桶下已有的存储桶标签。

#### 方法原型

```cpp
CosResult CosAPI::GetBucketTagging(const GetBucketTaggingReq& request, GetBucketTaggingResp* response);                                      
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::GetBucketTaggingReq req(bucket_name);
qcloud_cos::GetBucketTaggingResp resp;

qcloud_cos::CosResult result = cos.GetBucketTagging(req, &resp);

if (result.IsSucc()) {
    // 请求成功，通过 resp 的方法获取 Tagging
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

GetBucketTaggingResp 提供以下方法获取 Tagging

```
std::vector<Tag> GetTagSet() const;
```

#### 参数说明

| 参数 | 参数描述                   | 类型                | 是否必填  |
| ---- | ---------------------------| --------------------| ------|
| req  | GetBucketTagging 操作的请求 | GetBucketTaggingReq | 是    |
| resp | GetBucketTagging 操作的响应 | GetBucketTaggingResp| 是    |



## 删除存储桶标签

#### 功能说明

DELETE Bucket tagging 用于删除指定存储桶下已有的存储桶标签。

#### 方法原型

```cpp
CosResult CosAPI::DeleteBucketTagging(const DeleteBucketTaggingReq& request, DeleteBucketTaggingResp* response);                              
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::DeleteBucketTaggingReq req(bucket_name);
qcloud_cos::DeleteBucketTaggingResp resp;

qcloud_cos::CosResult result = cos.DeleteBucketTagging(req, &resp);

if (result.IsSucc()) {
    // 请求成功
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

#### 参数说明

| 参数 | 参数描述                      | 类型                   | 是否必填  |
| ---- | ------------------------------| -----------------------| ------|
| req  | DeleteBucketTagging 操作的请求 | DeleteBucketTaggingReq | 是    |
| resp | DeleteBucketTagging 操作的响应 | DeleteBucketTaggingResp| 是    |
