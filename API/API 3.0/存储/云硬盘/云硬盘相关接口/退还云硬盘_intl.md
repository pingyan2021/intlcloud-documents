## 1. API Description

Domain name for API request: cbs.tencentcloudapi.com.

This API (TerminateDisks) is used to return one or more cloud disks.

* You can use this API to return cloud disks that are no longer used.
* This API supports both monthly subscription and pay-as-you-go cloud disks. Pay-as-you-go cloud disks can be directly returned, and monthly subscription cloud disks must comply with the return rules.
* Batch operations are supported. The maximum number of cloud disks in a batch for each request is 50. If any cloud disk that does not allow batch operations exists in the batch, an error code is returned.

Default request rate limit: 20/sec.

Note: This API supports finance AZs. As finance AZs and non-finance AZs are isolated, when accessing the services in a finance AZ (with the common parameter Region specifying a financial availability zone), it is necessary to specify a domain name with the finance AZ, preferably in the same region as specified in Region.



## 2. Input Parameters

The list below contains only the API request parameters and certain common parameters. For the complete common parameter list, see [Common Request Parameters](/document/api/362/15637).

| Parameter Name | Required | Type | Description |
|---------|---------|---------|---------|
| Action | Yes | String | Common parameter. The value used for this API: TerminateDisks |
| Version | Yes | String | Common parameter. The value used for this API: 2017-03-12 |
| Region | Yes | String | Common parameter. For more information, see [List of Regions](/document/api/362/15637#.E5.9C.B0.E5.9F.9F.E5.88.97.E8.A1.A8) supported by the product. |
| DiskIds.N | Yes | Array of String | The list of IDs of cloud disks to be returned. |

## 3. Output Parameters

| Parameter Name | Type | Description |
|---------|---------|---------|
| RequestId | String | Unique ID of the request. Each request returns a unique ID. The RequestId is required to troubleshoot issues.  |

## 4. Samples

### Sample 1. Returning Cloud Disks in a Batch

#### Input Sample Code

```
https://cbs.tencentcloudapi.com/?Action=TerminateDisks
&DiskIds.0=disk-lzrg2pwi
&DiskIds.1=disk-g27hqeo2
&<Common request parameters>
```

#### Output Sample Code

```
{
  "Response": {
    "RequestId": "52c965d2-5deb-459a-8b5a-b3b9a1376544"
  }
}
```


## 5. Resources for Developers

### API Explorer

**This tool allows online call, signature authentication, SDK code generation and quick search of APIs to greatly improve the efficiency of using TencentCloud APIs.**

* [API 3.0 Explorer](https://console.cloud.tencent.com/api/explorer?Product=cbs&Version=2017-03-12&Action=TerminateDisks)

### SDK

TencentCloud API 3.0 comes with SDKs that support multiple programming languages and make it easier to call the APIs.

* [Tencent Cloud SDK 3.0 for Python](https://github.com/TencentCloud/tencentcloud-sdk-python)
* [Tencent Cloud SDK 3.0 for Java](https://github.com/TencentCloud/tencentcloud-sdk-java)
* [Tencent Cloud SDK 3.0 for PHP](https://github.com/TencentCloud/tencentcloud-sdk-php)
* [Tencent Cloud SDK 3.0 for Go](https://github.com/TencentCloud/tencentcloud-sdk-go)
* [Tencent Cloud SDK 3.0 for NodeJS](https://github.com/TencentCloud/tencentcloud-sdk-nodejs)
* [Tencent Cloud SDK 3.0 for .NET](https://github.com/TencentCloud/tencentcloud-sdk-dotnet)

### Command line tools

* [Tencent Cloud CLI 3.0](https://cloud.tencent.com/document/product/440/6176)

## 6. Error Codes

The following only lists the error codes related to this API. For other error codes, see [Common Error Codes](/document/api/362/15694#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81).

| Error Code | Description |
|---------|---------|
| InsufficientRefundQuota | Number of returned cloud disks has reached the limit and no more cloud disks can be returned. |
| InternalError.FailQueryResource | Failed to query the resource. |
| InvalidDisk.Expire | The cloud disk has expired. |
| InvalidDisk.NotSupportRefund | The cloud disk cannot be returned. |
| InvalidDisk.RepeatRefund | The cloud disk has been returned and cannot be returned again. |
| InvalidParameterValue | Invalid parameter value. Parameter value is in an incorrect format or is not supported. |
| MissingParameter | Missing parameter. A required parameter is missing in the request. |
