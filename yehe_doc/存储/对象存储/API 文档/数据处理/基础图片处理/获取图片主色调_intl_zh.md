## 功能描述

COS 通过数据万象 **imageAve** 接口获取图片主色调信息。目前支持大小在20M以内、长宽小于9999像素的图片处理。

>图片处理功能为收费项，由数据万象收取，详细的计费说明请参见数据万象 [计费与定价](https://intl.cloud.tencent.com/document/product/1045/33431)。

## 接口形式
```plaintext
download_url?imageAve       				
```

## 参数说明

**操作名称**：imageAve。

| 参数         | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| download_url | 文件的访问链接，具体构成为`<BucketName-APPID>.cos.<picture region>.<domain>.com/<picture name>`，<br>例如`examplebucket-1250000000.cos.ap-shanghai.myqcloud.com/picture.jpeg` |


## 实际案例

#### 请求

```plaintext
http://examples-1251000004.cos.ap-shanghai.myqcloud.com/sample.jpeg?imageAve
```

#### 响应
```plaintext
{"RGB": "0x736246"}
```
