>attachment.upload.config.json 附件统一上传接口相关配置

| 节点                  | 注释                                                            |
| :-------------------- | :-------------------------------------------------------------- |
| components[i].fileresource | 文件来源，主要用于区分不同文件系统上传的文件，同时作为文件上传时查找相关配置的依据，如文件上传时指明文件来源为WWZ，则对应下列配置中的第二个选项，`必填` |
| components[i].rootpath | 文件保存路径，可以是相对路径也可以是绝对路径，`必填` |
| components[i].originfolder | 原始文件所在文件夹名称，当文件需要经过处理并将原文件和处理后的文件分开保存时，此文件夹下保存原始文件，`选填` |
| components[i].processedfolder | 处理后文件所在文件夹名称，当文件需要经过处理并将原文件和处理后的文件分开保存时，此文件夹下保存处理过后的文件，`选填` |

```javascript
{
  "components": [
    {
      "fileresource": "YBG",
      "rootpath": "C:\\MyJob\\Upload\\YBG",
      "originfolder": "",
      "processedfolder": ""
    },
    {
      "fileresource": "WWZ",
      "rootpath": "Upload/WWZ",
      "originfolder": "",
      "processedfolder": ""
    }
  ]
}
```
