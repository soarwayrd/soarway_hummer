1. 先建立一个文件夹，并从git仓库内将hummer框架克隆到本地, 地址如下：
   >```git clone "ssh://sw.gerrit/soarway_hummer" && scp -p sw.gerrit:hooks/commit-msg "soarway_hummer/.git/hooks/"```
2. 打开soarway_hummer本地文件夹，找到`init_sln.bat`, 执行该bat，按照命令行打印出来的提示填写相关信息。cli会自动帮你**添加框架项目引用**及**初始化项目**。
   >第一步，输入你的解决方案文件夹名称：`soarway_demo`
   
   >第二步, 输入你的项目名称：`Demo`

   >第三步，输入框架所在文件夹名称：`soarway_hummer`

   >第四步, 静候cli批量跑完命令脚本，直到看到**请安任意键关闭...**字样，关闭cmd即可
3. 进入**soarway_demo**文件夹，打开**Soarway.Hummer.Demo.sln**文件，将**Soarway.Hummer.API**项目下的`Config`、`Certs`文件夹及`appSetting.json`,`nlog.config`文件拷贝至**Soarway.Hummer.Demo.API**项目下，并修改所有被拷贝的文件的VS文件属性为**如果较新则复制**
4. 修改**Soarway.Hummer.Demo.API**项目的`Program.cs`和`Startup.cs`如下
   ### Program.cs
   ```C#
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args)
        {
            return Core.API.Program.CreateBaseWebHostBuilder(args)
                                   .UseStartup<Startup>()
								   //限制HTTP请求主体的最大尺寸
                                   .UseKestrel(options => { options.Limits.MaxRequestBodySize = AppSettings.Get<int>(ConfigKey.MaxRequestBodySize) * 1024; });
        }
    }
   ```

   ### Startup.cs
   ```C#
   public class Startup : Core.API.BaseStartup
   {
       public Startup(IConfiguration configuration) : base(configuration)
       {
           Configuration = configuration;
       }

       public override IConfiguration Configuration { get; }

       public override IServiceProvider ConfigureServices(IServiceCollection services)
       {
           return base.ConfigureServices(services);
       }

       public override void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
       {
           base.Configure(app, env, loggerFactory);
       }
   }
   ```
5. 若需要修改启动端口，可编辑`appSetting.json`的`system.url`配置
   >注意：`system.url`的**IP**或**域名**不能使用通配符\*来表示，必须写上完整的ip地址或localhost。推荐使用`http://[ip]:[port]`的方式来完整的表示绑定IP及端口
6. 至此, 项目框架就算是搭建完毕了，我们可以写一个测试接口测试下自定义的接口能否被正常调用。
   >[快速开始](SUMMARY.md),至此介绍完毕。你可以开始根据框架给您提供的模板项目编写自己的业务逻辑了。但为了更好的进行快速开发，还是推荐您继续阅读[最佳实践](\最佳实践.md)章节的内容。