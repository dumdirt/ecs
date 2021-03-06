# ModifySecurityGroupPolicy {#doc_api_1031578 .reference}

Modifies the intranet communication policy of a security group.

## Description {#description .section}

When you call this operation, note that:

-   When the InnerAccessPolicy parameter value is Accept, instances within the security group can communicate with each other. The Accept policy has the highest priority of all rules, and all other user-defined rules are ignored.
-   When the InnerAccessPolicy value is Drop, instances in the security group are isolated from each other. In this case, user-defined security group rules have a higher priority and can be used to change the intranet access policy. For example, you can use [AuthorizeSecurityGroup](~~25554~~) to allow ECS instances in the security group to communicate with each other.
-   You can use [DescribeSecurityGroupAttribute](~~25555~~) to query the intranet communication policy of the security group.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=ModifySecurityGroupPolicy) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|InnerAccessPolicy|String|Yes|Accept| The intranet communication policy of the security group. Valid values:

 -   Accept: Instances in the security group can communicate with each other.
-   Drop: Instances in the security group are isolated from each other.

 The values are case-insensitive.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region where the security group resides. You can call [DescribeRegions](~~25609~~) to view the latest regions of Alibaba Cloud.

 |
|SecurityGroupId|String|Yes|sg-securitygroupid1| The ID of the security group.

 |
|Action|String|No|ModifySecurityGroupPolicy| The operation that you want to perform. Set the value to ModifySecurityGroupPolicy.

 |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000| A client token. It is used to ensure the idempotency of requests. The value of this parameter is generated by the client and is unique among different requests. The **ClientToken** parameter must be no more than 64 ASCII characters in length. For more information, see [How to ensure idempotency](~~25693~~).

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=ModifySecurityGroupPolicy
&RegionId=cn-hangzhou 
&SecurityGroupId=sg-1133aa
&InnerAccessPolicy=Drop
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<ModifySecurityGroupPolicyResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BZ015</RequestId>
</ModifySecurityGroupPolicyResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_c56_qlf_2li .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidSecurityGroupId.Malformed|The SecurityGroupId is invalid. Only letters, numbers and underscores are supported. Maximum length is 100 characters.|The error message returned when the security group ID is invalid.|
|400|InvalidPolicy.Malformed|The Policy is invalid. Only 'Accept' and 'Drop' are supported. Ignore case.|The error message returned when the Policy parameter value is invalid.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

