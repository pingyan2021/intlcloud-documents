## 1. API Description

This API (RejectVpcPeeringConnectionEx) is used to reject cross-region peering connections.
API request domain name: <font style="color:red">vpc.api.qcloud.com</font>

This API is used by the receiver to reject the request for cross-region peering connection from another account.

## 2. Input Parameters
Below is a list of API request parameters. You need to add common request parameters to your request when calling this API. For more information, see the <a href=" https://intl.cloud.tencent.com/doc/api/372/4153" title="Common Request Parameters">Common Request Parameters</a> page. The Action field for this API is RejectVpcPeeringConnectionEx.

| Parameter name | Required | Type | Description |
|---------|---------|---------|---------|
| peeringConnectionId | Yes | String | ID of VPC peering connection, for example: pcx-8g675gr8. |


## 3. Output Parameters

| Parameter name | Type | Description |
|---------|---------|---------|
| code | int | Error code. 0: Successful; other values: Failed. |
| message | string | Error message. |
| taskId | int | Task ID. You can query the execution result by using taskId. For more information, see the <a href="https://intl.cloud.tencent.com/doc/api/245/%e6%9f%a5%e8%af%a2%e4%bb%bb%e5%8a%a1%e6%89%a7%e8%a1%8c%e7%bb%93%e6%9e%9c%e6%8e%a5%e5%8f%a3">API for Querying Task Execution Results</a>. |

## 4. Error Codes
  The following error codes only include business logic error codes for this API. For additional common error codes, see <a href="https://intl.cloud.tencent.com/doc/api/245/4924" title="VPC Error Codes">VPC Error Codes</a>.
	
| Error code | Description |
|---------|---------|
| InvalidVpc.NotFound | Invalid VPC. This error code indicates that the VPC resource does not exist. In this case, verify whether the resource information that you entered is correct. |
| InvalidPeeringConnection.NotFound | Invalid peering connection. This error code indicates that the peering connection resource does not exist. In this case, verify whether the resource information that you entered is correct. |

## 5. Sample
Input
<pre>
https://vpc.api.qcloud.com/v2/index.php?Action=RejectVpcPeeringConnectionEx
&<<a href="https://intl.cloud.tencent.com/doc/api/229/6976">Common Request Parameters</a>>
&peeringConnectionId=pcx-8g675gr8
</pre>
Output
```
{
    "code":"0",
    "message":"",
    "taskId":1235
}
```

