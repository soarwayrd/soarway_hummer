>Execl导出数据Headers配置

>Execl下载实现该功能主要是在拦截器判断*ExportFile*当为true的时候就到下载的数据的功能。

1. 当前列表数据下载需要在Headers设置，这个配置针对当前页面的数据下载比如这个页面只显示10条数据就只会下载10条数据。

**Headers**参数设置

| Key        | VALUE                                       |
| :--------- | :------------------------------------------ |
| ExportFile | 下载传`true`,不要下载`ExportFile`字段不要传 |
| Columns    | {"UserName":"用户名称","Cellphone":"电话"}  |

2. 分页数据下载需要在Headers设置size、num这二个参数主要是分页时下载数据的时候配置，比如num=1，size=100，就会下载100条数据。

**Headers**参数设置

| Key        | VALUE                                                 |
| :--------- | :---------------------------------------------------- |
| ExportFile | 下载传`true`,不要下载`ExportFile`字段不要传           |
| size       | `size`                                                |
| num        | `num`                                                 |
| Columns    | {"UserName":"用户名称","Cellphone":"电话","LockDate"} |

**Columns说明** `UserName`为数据库字段名称，`用户名称`导到execl列头名称。Columns里的数据需要`UrlEncode`编码。

编码后的数据：
`%7b%22UserName%22%3a%22%e7%94%a8%e6%88%b7%e5%90%8d%e7%a7%b0%22%2c%22Cellphone%22%3a%22%e7%94%b5%e8%af%9d%22%7d`
