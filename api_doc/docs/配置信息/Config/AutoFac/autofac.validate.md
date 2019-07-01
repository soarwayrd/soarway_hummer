>autofac.validate.config.json 配置与验证相关的依赖注入

| 节点                           | 注释                                                             |
| :----------------------------- | :--------------------------------------------------------------- |
| components[i].type             | 依赖注入的具体实现类全称(`FullName`)及程序集名称(`AssemblyName`) |
| components[i].services[j].type | 依赖注入的抽象接口全称(`FullName`)及程序集名称(`AssemblyName`)   |


```javascript
{
  "components": [
    {
      "type": "Soarway.Hummer.Core.Infrastructure.RedisAuthorization, Soarway.Hummer.Core.Infrastructure",
      "services": [
        {
          "type": "Soarway.Hummer.Core.Infrastructure.IValidateAuthorization, Soarway.Hummer.Core.Infrastructure"
        }
      ]
    },
    {
      "type": "Soarway.Hummer.Core.Infrastructure.VcomSmsSent, Soarway.Hummer.Core.Infrastructure",
      "services": [
        {
          "type": "Soarway.Hummer.Core.Infrastructure.ISentSms, Soarway.Hummer.Core.Infrastructure"
        }
      ]
    },
    {
      "type": "Soarway.Hummer.Core.Infrastructure.RedisManager, Soarway.Hummer.Core.Infrastructure",
      "services": [
        {
          "type": "Soarway.Hummer.Core.Infrastructure.ICacheManager, Soarway.Hummer.Core.Infrastructure"
        }
      ]
    }
  ]
}
```