>? **当前页面接口为旧版 API，未来可能停止维护，目前不展示在左侧导航。云服务器 API 3.0 版本接口定义更加规范，访问时延下降显著，建议使用 <a href="https://intl.cloud.tencent.com/document/api/213/15689" target="_blank">云服务器 API 3.0</a>。**
>


若 API 调用失败，则最终返回结果中的错误码 code 不为 0，message 字段会显示详细错误信息。用户可以根据 code 和 message 在 [错误码](https://intl.cloud.tencent.com/document/product/377/8946) 页面查询具体的错误信息。
错误返回示例如下：

```
{
    "code": "5100",
    "message": "(100004)projectId不正确"
}
```
