## 简介

本文档提供关于查询对象元数据操作相关的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名         | 操作描述                                  |
| ------------------------------------------------------------ | -------------- | ----------------------------------------- |
| [HEAD Object](https://intl.cloud.tencent.com/document/product/436/7745) | 查询对象元数据 | 查询对象的元数据信息                  |

## SDK API 参考

SDK 所有接口的具体参数与方法说明，请参考 [SDK API](https://cos-dotnet-sdk-doc-1253960454.file.myqcloud.com/)。

## 查询对象元数据

#### 功能说明

查询 Object 的 Meta 信息。

#### 示例代码

[//]: # (.cssg-snippet-head-object)
```cs
try
{
  string bucket = "examplebucket-1250000000"; //存储桶，格式：BucketName-APPID
  string key = "exampleobject"; //对象键
  HeadObjectRequest request = new HeadObjectRequest(bucket, key);

  //执行请求
  HeadObjectResult result = cosXml.HeadObject(request);
  //请求成功
  Console.WriteLine(result.GetResultInfo());
}
catch (COSXML.CosException.CosClientException clientEx)
{
  //请求失败
  Console.WriteLine("CosClientException: " + clientEx);
}
catch (COSXML.CosException.CosServerException serverEx)
{
  //请求失败
  Console.WriteLine("CosServerException: " + serverEx.GetInfo());
}
```

>?更多完整示例，请前往 [GitHub](https://github.com/tencentyun/cos-snippets/tree/master/dotnet/dist/HeadObject.cs) 查看。

