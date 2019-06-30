>autofac.repository.config.json 主要配置仓储的依赖注入

以下配置以UserRepository为例，展示如何配置UserRepository

| 节点                           | 注释                                                             |
| :----------------------------- | :--------------------------------------------------------------- |
| components[i].type             | 依赖注入的具体实现类全称(`FullName`)及程序集名称(`AssemblyName`) |
| components[i].services[j].type | 依赖注入的抽象接口全称(`FullName`)及程序集名称(`AssemblyName`)   |
|                                |                                                                  |

```javascript
{
  "components": [
    //UserRepository
    {
      "type": "Soarway.Hummer.Core.Repository.EF.UserRepository, Soarway.Hummer.Core.Repository.EF",
      "services": [
        {
          "type": "Soarway.Hummer.Core.IRepository.IUserRepository, Soarway.Hummer.Core.IRepository"
        }
      ]
    }
  ]
}
```