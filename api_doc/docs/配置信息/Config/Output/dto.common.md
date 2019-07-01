>dto.*.config.json 配置框架接口的返回值

以获取User表分页数据为例，框架定义的API地址[http://localhost:5100/api/users/num/1/size/20](http://localhost:5100/api/users/num/1/size/10)

默认返回值为User全表字段
```javascript
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
    "CreateDate": "2019-06-18T15:29:09.483",
    "IdCard": null,
    "Avatar": null
}
```
假设其中的`IdCard`, `Avatar`字段是其他项目组引入，对您的项目组而言，这两个字段却是个冗余，你不希望在API接口的返回值里体现，此时可以通过在`config\output`文件夹内定义`dto.UserQueryResultDTO.config.json`，并修改文件属性为**如果较新则复制**，文件内加入如下配置：

```javascript
{
  "IdCard": false,
  "Avatar": false
}
```

>注意：该配置对文件名有要求，必须是dbset.*.config.json的文件名格式,其中 \* 为通配符，为接口返回值的类型。以本例为例，\* 就为UserQueryResultDTO, 最后配置文件的文件名全名为`dto.UserQueryResultDTO.config.json`

再次调用该API接口，返回值里`IdCard`,`Avatar`将会被精简掉

```javascript
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

