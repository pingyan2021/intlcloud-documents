

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

```
put_bucket_website(Bucket, WebsiteConfiguration={}, **kwargs)
```

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-website)
```py
response = client.put_bucket_website(
    Bucket='bucket',
    WebsiteConfiguration={
        'IndexDocument': {
            'Suffix': 'string'
        },
        'ErrorDocument': {
            'Key': 'string'
        },
        'RedirectAllRequestsTo': {
            'Protocol': 'http'|'https'
        },
        'RoutingRules': [
            {
                'Condition': {
                    'HttpErrorCodeReturnedEquals': 'string',
                    'KeyPrefixEquals': 'string'
                },
                'Redirect': {
                    'HttpRedirectCode': 'string',
                    'Protocol': 'http'|'https',
                    'ReplaceKeyPrefixWith': 'string',
                    'ReplaceKeyWith': 'string'
                }
            }
        ]
    }
)
```

#### 参数说明

| 参数名称                    | 参数描述                                                     | 类型   | 是否必填 |
| --------------------------- | ------------------------------------------------------------ | ------ | -------- |
| Bucket                      | 设置静态网站的存储桶，格式为 BucketName-APPID ，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String | 是       |
| IndexDocument               | 设置静态网站首页的配置                                       | Dict   | 是       |
| Suffix                      | 静态网站首页地址的后缀配置                                   | String | 是       |
| ErrorDocument               | 设置静态网站错误页面配置                                     | Dict   | 否       |
| Key                         | 错误页面地址                                                 | String | 否       |
| RedirectAllRequestsTo       | 设置全站重定向配置                                           | Dict   | 否       |
| Protocol                    | 全站重定向协议，可选值为 http、https                          | String | 否       |
| RoutingRules                | 设置静态网站路由规则                                         | List   | 否       |
| Condition                   | 路由的条件,包括错误码重定向和前缀重定向                      | Dict   | 否       |
| HttpErrorCodeReturnedEquals | 错误码重定向的条件                                           | String | 否       |
| KeyPrefixEquals             | 前缀重定向的条件                                             | String | 否       |
| Redirect                    | 重定向的具体规则                                             | Dict   | 否       |
| HttpRedirectCode            | 重定向时的错误码                                             | String | 否       |
| Protocol                    | 重定向的协议，可选值为 http、https                             | String | 否       |
| ReplaceKeyPrefixWith        | 重定向时替换前缀为指定的 key                                  | String | 否       |
| ReplaceKeyWith              | 重定向时替换整个路径为指定的 key                              | String | 否       |

#### 返回结果说明

该方法返回值为 None。

## 查询静态网站配置

#### 功能说明

GET Bucket website 用于查询与存储桶关联的静态网站配置信息。

#### 方法原型

```
get_bucket_website(Bucket, **kwargs)
```

#### 请求示例

[//]: # (.cssg-snippet-get-bucket-website)
```
response = client.get_bucket_website(
    Bucket='examplebucket-1250000000'
)
```

#### 参数说明                        |

| 参数名称 | 参数描述                                                     | 类型   | 是否必填 |
| -------- | ------------------------------------------------------------ | ------ | -------- |
| Bucket   | 查询静态网站配置的存储桶，格式为 BucketName-APPID ，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String | 是       |

#### 返回结果说明

Bucket 静态网站配置，类型为 dict。

```
{
    'IndexDocument': {
        'Suffix': 'string'
    },
    'ErrorDocument': {
        'Key': 'string'
    },
    'RedirectAllRequestsTo': {
        'Protocol': 'http'|'https'
    },
    'RoutingRules': [
        {
            'Condition': {
                'HttpErrorCodeReturnedEquals': 'string',
                'KeyPrefixEquals': 'string'
            },
            'Redirect': {
                'HttpRedirectCode': 'string',
                'Protocol': 'http'|'https',
                'ReplaceKeyPrefixWith': 'string',
                'ReplaceKeyWith': 'string'
            }
        }
    ]
}
```

| 参数名称                    | 参数描述                                 | 类型   |
| --------------------------- | ---------------------------------------- | ------ |
| IndexDocument               | 设置静态网站首页的配置                   | Dict   |
| Suffix                      | 静态网站首页地址的后缀配置               | String |
| ErrorDocument               | 设置静态网站错误页面配置                 | Dict   |
| Key                         | 错误页面地址                             | String |
| RedirectAllRequestsTo       | 设置全站重定向配置                       | Dict   |
| Protocol                    | 全站重定向协议，可选值为 http、https      | String |
| RoutingRules                | 设置静态网站路由规则                     | List   |
| Condition                   | 路由的条件，包括错误码重定向和前缀重定向 | Dict   |
| HttpErrorCodeReturnedEquals | 错误码重定向的条件                       | String |
| KeyPrefixEquals             | 前缀重定向的条件                         | String |
| Redirect                    | 重定向的具体规则                         | Dict   |
| HttpRedirectCode            | 重定向时的错误码                         | String |
| Protocol                    | 重定向的协议，可选值为 http、https        | String |
| ReplaceKeyPrefixWith        | 重定向时替换前缀为指定的 key             | String |
| ReplaceKeyWith              | 重定向时替换整个路径为指定的 key         | String |

## 删除静态网站配置

#### 功能说明

DELETE Bucket website 用于删除存储桶中的静态网站配置。

#### 方法原型

```
delete_bucket_website(Bucket, **kwargs)
```

#### 请求示例

[//]: # (.cssg-snippet-delete-bucket-website)
```
response = client.delete_bucket_website(
    Bucket='examplebucket-1250000000'
)
```

#### 参数说明

| 参数名称 | 参数描述                                                     | 类型   | 是否必填 |
| -------- | ------------------------------------------------------------ | ------ | -------- |
| Bucket   | 被删除静态网站配置的存储桶，格式为 BucketName-APPID ，详情请参见 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String | 是       |

#### 返回结果说明

该方法返回值为 None。
