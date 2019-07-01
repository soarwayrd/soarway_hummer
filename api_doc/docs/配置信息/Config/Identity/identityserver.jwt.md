>identityserver.jwt.config.json 配置与IdentityServer4颁发Jwt令牌


| 节点                                      | 注释                                          |
| :---------------------------------------- | :-------------------------------------------- |
| identityServerConfig.resources[i].name    | Api资源的名称                                 |
| identityServerConfig.resources[i].display | Api资源的展示文本                             |
| identityServerConfig.clients[i].id        | 客户端id，类似于微信第三方应用的appID         |
| identityServerConfig.clients[i].secrets   | 客户端的秘钥，类似于微信第三方应用的appSecret |
| identityServerConfig.clients[i].scopes    | 客户端请求的作用域                            |


```javascript
{
  "identityServerConfig": {
    "resources": [
      {
        "name": "hummer.core.api",
        "display": "hummer.core.api"
      }
    ],
    "clients": [
      {
        "id": "hummer.core.api",
        "secrets": "secret",
        "scopes": "hummer.core.api"
      }
    ]
  }
}
```

>对项目组而言，关心的节点配置一般是`identityServerConfig.clients`里的id,secrets,scopes三个
