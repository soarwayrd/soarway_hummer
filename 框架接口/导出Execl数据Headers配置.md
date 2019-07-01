>接口导出Execl数据Headers配置

分页接口请求地址如 **http://localhost:5100/api/users/num/1/size/6**

**GET**请求

**Headers**参数设置

| 节点       | 注释                                                  |
| :--------- | :---------------------------------------------------- |
| ExportFile | 下载传`true`,不要下载`ExportFile`字段不要传           |
| size       | `size`                                                |
| num        | `num`                                                 |
| Columns    | {"UserName":"用户名称","Cellphone":"电话","LockDate"} |

**Columns说明** UserName为数据库字段名称，`用户名称`导到execl列头名称。Columns里的数据需要`UrlEncode`编码。
编码后的数据`%7b%22UserName%22%3a%22%e7%94%a8%e6%88%b7%e5%90%8d%e7%a7%b0%22%2c%22Cellphone%22%3a%22%e7%94%b5%e8%af%9d%22%7d`
