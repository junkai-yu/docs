# 获取用户实名认证信息

<!--
  警告⚠️：
  不要直接修改该文档，
  https://github.com/Authing/authing-docs-factory
  使用该项目进行生成
-->

<LastUpdated />

获取用户实名认证信息

## 请求参数

| 名称 | 类型 | 必填 | 默认值 | 描述 |
| ---- | ---- | ---- | ---- | ---- |
| userId | string  | 是 |  | 用户 ID。 示例值： `6229ffaxxxxxxxxcade3e3d9` |


## 示例代码

```ts
import { ManagementClient } from 'authing-node-sdk';
// 在 Node.js 中引用：
// const { ManagementClient } = require('authing-node-sdk');

const managementClient = new ManagementClient({
  accessKeyId: 'AUTHING_USERPOOL_ID',
  accessKeySecret: 'AUTHING_USERPOOL_SECRET',
});

(async () => {
  const result = await managementClient.getUserPrincipalAuthenticationInfo({

    userId: '6229ffaxxxxxxxxcade3e3d9',
 });
})();
```



## 请求响应

类型： `PrincipalAuthenticationInfoPaginatedRespDto`

| 名称 | 类型 | 描述 |
| ---- | ---- | ---- |
| statusCode | number | 业务状态码，可以通过此状态码判断操作是否成功，200 表示成功。 |
| message | string | 描述信息 |
| apiCode | number | 细分错误码，可通过此错误码得到具体的错误类型。 |
| data | <a href="#PrincipalAuthenticationInfoPagingDto">PrincipalAuthenticationInfoPagingDto</a> | 响应数据 |



示例结果：

```json
{
  "statusCode": 200,
  "message": "操作成功",
  "apiCode": 20001,
  "data": {
    "list": {
      "authenticated": true,
      "principalType": "认证主体类型，P 代表个人，E 代表企业",
      "principalCode": "6229c4deb3e4d8a20b6021ff",
      "principalName": "ss",
      "authenticatedAt": "2022-04-05T10:23:50.631Z"
    }
  }
}
```

## 数据结构


### <a id="PrincipalAuthenticationInfoPagingDto"></a> PrincipalAuthenticationInfoPagingDto

| 名称 | 类型 | 必填 | 描述 |
| ---- |  ---- | ---- | ---- |
| totalCount | number | 是 | 记录总数。   |
| list | array | 是 | 响应数据。嵌套类型：<a href="#PrincipalAuthenticationInfoDto">PrincipalAuthenticationInfoDto</a>。   |


### <a id="PrincipalAuthenticationInfoDto"></a> PrincipalAuthenticationInfoDto

| 名称 | 类型 | 必填 | 描述 |
| ---- |  ---- | ---- | ---- |
| authenticated | boolean | 是 | 是否进行认证。 示例值： `true`  |
| principalType | string | 是 | 用户 ID。 示例值： `认证主体类型，P 代表个人，E 代表企业`  |
| principalCode | string | 是 | 认证主体证件号码。 示例值： `6229c4deb3e4d8a20b6021ff`  |
| principalName | string | 是 | 认证主体名称。 示例值： `ss`  |
| authenticatedAt | string | 是 | 认证时间，标准时间字符串。 示例值： `2022-04-05T10:23:50.631Z`  |


