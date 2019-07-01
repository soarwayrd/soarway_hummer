>database.core.config.json 配置数据Sql Server库链接字符串与Redis链接配置

| 节点                   | 注释                                                |
| :--------------------- | :-------------------------------------------------- |
| dbCore                 | 数据库链接字符串                                    |
| redis.password         | 设置**redis**密码,密码为空可以注释password          |
| redis.allowAdmin       | 启用被认定为是有风险的一些命令                      |
| redis.ssl              | 使用SSL加密                                         |
| redis.connectTimeout   | 链接超时时间                                        |
| redis.connectRetry     | 在初始化 `Connect` 失败的时候重新尝试进行链接的次数 |
| redis.database         | 默认的数据库                                        |
| redis.hosts[i].host    | redis数库链接字符串                                 |
| redis.hosts[i].port    | redis链接端口                                       |
| cacheDb.token_validate | identityserver生成的token数据写到redis服务 `db0`    |
| cacheDb.api_auth       | 接口请求资源数据写到redis服务 `db1`                 |


```javascript
{
  "dbCore": "Server=192.168.0.220;Database=SmartBuilding;Integrated Security=false;User ID=sa;   Password=SoarwayDB",
  "redis": {
    "password": "654321",
    "allowAdmin": true,
    "ssl": false,
    "connectTimeout": 6000,
    "connectRetry": 2,
    "database": 0,
    "hosts": [
      {
        "host": "127.0.0.1",
        "port": "6379"
      }
    ]
  },
  "cacheDb": {
    "token_validate": 0,
    "api_auth": 1
  }
}
```