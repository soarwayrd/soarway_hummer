>autofac.automapper.config.json主要配置框架及项目的对象映射组件

配置是基于[autofac](https://autofac.readthedocs.io/en/latest/configuration/xml.html#configuring-with-microsoft-configuration-4-0)容器组件。

各业务模块若有自己的[AutoMapper](http://docs.automapper.org/en/stable/Getting-started.html)映射配置,应继承并实现`ISoarwayMapper`,并将实现了`ISoarwayMapper`接口的实现类配置到`autofac.automapper.config.json`文件内。

多个[AutoMapper](http://docs.automapper.org/en/stable/Getting-started.html)映射配置，则可在`autofac.automapper.config.json`文件的`components`节点内按示例规则继续添加。



| 节点                           | 注释                                                             |
| :----------------------------- | :--------------------------------------------------------------- |
| components[i].type             | 依赖注入的具体实现类全称(`FullName`)及程序集名称(`AssemblyName`) |
| components[i].services[j].type | 依赖注入的抽象接口全称(`FullName`)及程序集名称(`AssemblyName`)   |
|                                |                                                                  |

```javascript
{
  "components": [
    {
      "type": "Soarway.Hummer.Core.Infrastructure.SoarwayMapper, Soarway.Hummer.Core.Infrastructure",
      "services": [
        {
          "type": "Soarway.Hummer.Core.Infrastructure.ISoarwayMapper, Soarway.Hummer.Core.Infrastructure"
        }
      ]
    }
  ]
}
```