## 功能描述

本接口用于删除日志集。

## 请求

#### 请求示例

```shell
DELETE /logset?logset_id=xxxx-xx-xx-xx-xxxxxxxx HTTP/1.1
Host: <Region>.cls.tencentyun.com
Authorization: <AuthorizationString>
```

#### 请求行

```shell
DELETE /logset
```

#### 请求头

除公共头部外，无特殊请求头部。

#### 请求参数

| 字段名        |  类型  | 位置  | 必须 |      含义                       |
|--------------|--------|------|---------|--------------------------------|
| logset_id    | string | query| 是      |要删除的日志集的 ID                |

## 响应

#### 响应示例

```shell
HTTP/1.1 200 OK
Content-Length: 0
```

#### 响应头

除公共响应头部外，无特殊响应头部。

#### 响应参数

如果删除成功，无响应参数。

## 错误码

参见 [错误码](https://intl.cloud.tencent.com/document/product/614/12402)。
