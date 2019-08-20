#### redis 开启远程访问权限

1. 找到*redis.windows-service.conf*文件，将*redis.windows-service.conf* 里的 bind 127.0.0.1 这一行注释掉，任意IP都可以访问；找到 protected-mode yes 改为 protected-mode no；保存之后重启redis。
   
   ![GitHub](../accets/redissetting.png)
