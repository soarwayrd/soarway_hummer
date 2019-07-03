>appSetting.json主要配置框架级别的通用配置项

```javascript
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "system": {
    "url": "http://localhost:5100",
    "name": "智慧楼宇API"
  },
  "certificates": {
    "cerPath": "certs\\soarway.core.pfx",
    "password": "cm123456"
  },
  "isWrapOutput": true,
  "maxRequestBodySize": "20000" //限制HTTP请求主体的最大尺寸(单位KB)
}
```
| 节点                  | 注释                                                                                                                          |
| :-------------------- | :---------------------------------------------------------------------------------------------------------------------------- |
| system.url            | 宿主容器启动地址及端口号，注意此处**不能使用**`http://*:5100`的方式来描述，会导致IdentityServer4的验签服务出错。              |
| system.name           | 系统名称，这段文本会在SwaggerUI的标题里展示。                                                                                 |
| certificates.cerPath  | IdentityServer4所使用的的整数文件路径，一般放置于宿主容器项目下的Certs文件夹内即可，并将pfx文件的属性改为**如果较新则复制**。 |
| certificates.password | pfx证书的密码                                                                                                                 |
| isWrapOutput          | `true`:返回值包含**接口状态信息**和**业务数据**，`false`:**只返回业务数据**                                                   |
| maxRequestBodySize    | 限制HTTP请求主体的最大尺寸(单位KB)，主要用于限制附件上传大小                                                                    |
```javascript
// isWrapOutput:true, 多返回一个status对象
{
    "result": [
        {
            "UserName": "test123",
            "Cellphone": "12344",
            "Gender": false,
            "Enable": true,
            "IsPc": false,
            "IsMobile": false,
            "IsLock": false,
            "FailtCount": 0,
            "LockDate": null,
            "CreateDate": "2019-06-18T15:29:09.483"
        }
    ],
    "page": {
        "count": 1,
        "num": 1,
        "size": 20
    },
    "status": {
        "timeSpan": 77,
        "isSuccess": true,
        "actionMsg": {},
        "modelMsg": {},
        "errorMsg": {}
    }
}
```


```C#
{
    "UserName": "test123",
    "Cellphone": "12344",
    "Gender": false,
    "Enable": true,
    "IsPc": false,
    "IsMobile": false,
    "IsLock": false,
    "FailtCount": 0,
    "LockDate": null,
    "CreateDate": "2019-06-18T15:29:09.483"
}
```