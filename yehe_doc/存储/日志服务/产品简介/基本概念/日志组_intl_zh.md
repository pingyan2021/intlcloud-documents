日志组（LogGroup）是一个包含多条日志的集合。在上传、消费日志的过程中，考虑读写的效率和压力，日志组作为 CLS 基本的数据单元，可将多条日志打包成一个日志组，并以日志组为单位发送到 CLS 。

一个日志组里的日志具有相同的元信息（\_\_FILENAME__、\_\_SOURCE\_\_、\_\_LogTag\_\_等），详细参考上传数据结构 [CLS Protobuf 数据格式](https://intl.cloud.tencent.com/document/product/614/16873)。

相关限制：

- 一个数据包里 [LogGroup ](https://intl.cloud.tencent.com/document/product/614/16873) 包含日志条数至少为1条，最多为10000条
-  LogGroup 所有 Value 大小最大总和为5MB

  

  

