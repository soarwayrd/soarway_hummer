>获取token配置与获取refresh_token配置

**获取token配置**

token地址[http://localhost:5100/connect/token]

**http://localhost:5100**配置在appSetting.json节点system.url配置的地址

**POST**请求

Body里的**from-data**格式

| 节点                  | 注释                                                            |
| :-------------------- | :-------------------------------------------------------------- |
| client_id | hummer.core.api (配置在**appSetting.json**节点identityServerConfig.resources[i].name) |
| client_secret | secret |
| grant_type | password (账号密码方法验证) |
| username | test123 (P_User表的用户名) |
| password | 123456 (P_User表的密码)密码写到数据库是是md5加密的在postman请求的时候可以明文 |

```javascript
{
    "access_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6IkJCMTdGQkQ3NUE5NkRFMjMyOEEwOTgwNDc0QUM3QkQzRTY4RUVENzEiLCJ0eXAiOiJKV1QiLCJ4NXQiOiJ1eGY3MTFxVzNpTW9vSmdFZEt4NzAtYU83WEUifQ.eyJuYmYiOjE1NjE5NDgxNTksImV4cCI6MTU2MTk1MTc1OSwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo1MTAwIiwiYXVkIjpbImh0dHA6Ly9sb2NhbGhvc3Q6NTEwMC9yZXNvdXJjZXMiLCJodW1tZXIuY29yZS5hcGkiXSwiY2xpZW50X2lkIjoiaHVtbWVyLmNvcmUuYXBpIiwic3ViIjoidGVzdDEyMyIsImF1dGhfdGltZSI6MTU2MTk0ODE1OSwiaWRwIjoibG9jYWwiLCJ1c2VyX2lkIjoiMSIsIm5hbWUiOiJ0ZXN0MTIzIiwiaWQiOiIxIiwicm9sZSI6IjUiLCJzY29wZSI6WyJodW1tZXIuY29yZS5hcGkiLCJvZmZsaW5lX2FjY2VzcyJdLCJhbXIiOlsiY3VzdG9tIl19.WFxpfxhbS-kQNq5jK2JaBqVI94EtvSGRWU9QkbeunT-AQ5j9EAw1ifbJFrU-G_6J1jVohNkbGLNHQLY_Nb_M3tYnQZu1SLATkNcyo5H4QF9YGTHVMSe5zmAsuYI_Os67doGQBGdX15Ex66nnaNt298rzbYfgynqmSxjyl1Cp3AYihbSIwoa2JgL3RM9nM96jsXKzkPWsdLYLlqqbEHCiBPOVa_SpuxXOU4QyELOGpT6Oy6U-7346r2PtCtlipGmcjCQ1q4zq6WF5RJ6AfgTEI3SijlNTV5-me6qoqfnSe9qVlAM31fE7N8sbP8l5kCohxd_-kHaabn25f4Q4cjIxOA",
    "expires_in": 3600,
    "token_type": "Bearer",
    "refresh_token": "faa2612d4789067176cce12a207a5b9e11f6adaada8764b59b3f0e5905dcf92c"
}
```

**获取refresh_token配置**

token地址[http://localhost:5100/connect/token]

**http://localhost:5100**配置在appSetting.json节点system.url配置的地址

**POST**请求

Body里的**from-data**格式

| 节点                  | 注释                                                            |
| :-------------------- | :-------------------------------------------------------------- |
| client_id | hummer.core.api (配置在**appSetting.json**节点identityServerConfig.resources[i].name) |
| client_secret | secret |
| grant_type | refresh_token (上面获取的**refresh_token**) |
| refresh_token | faa2612d4789067176cce12a207a5b9e11f6adaada8764b59b3f0e5905dcf92c |

```javascript
{
    "access_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6IkJCMTdGQkQ3NUE5NkRFMjMyOEEwOTgwNDc0QUM3QkQzRTY4RUVENzEiLCJ0eXAiOiJKV1QiLCJ4NXQiOiJ1eGY3MTFxVzNpTW9vSmdFZEt4NzAtYU83WEUifQ.eyJuYmYiOjE1NjE5NTI4MDYsImV4cCI6MTU2MTk1NjQwNiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo1MTAwIiwiYXVkIjpbImh0dHA6Ly9sb2NhbGhvc3Q6NTEwMC9yZXNvdXJjZXMiLCJodW1tZXIuY29yZS5hcGkiXSwiY2xpZW50X2lkIjoiaHVtbWVyLmNvcmUuYXBpIiwic3ViIjoidGVzdDEyMyIsImF1dGhfdGltZSI6MTU2MTk1MjgwMSwiaWRwIjoibG9jYWwiLCJ1c2VyX2lkIjoiMSIsIm5hbWUiOiJ0ZXN0MTIzIiwiaWQiOiIxIiwicm9sZSI6IjUiLCJzY29wZSI6WyJodW1tZXIuY29yZS5hcGkiLCJvZmZsaW5lX2FjY2VzcyJdLCJhbXIiOlsiY3VzdG9tIl19.ZSY1RwAOeRERqVp0VlfVCFpNG2j4gBGUFU8p7y4LCXmkH_RoGcMUPU13BYpKxeSOQuc5_k2enVOgRzAzjRb5ExAWamm9UGRt2lvh95DK8bCkzk7dP7LeL6GQDvoe4PFWfJntbLhnGF5wjUHgWou2v7Xw9CadLd5vRE9VxNPwgsv5qwZifiW5G8bdAySz40_UJjED8DcinQLOheCg1rUG6gsblM4VKF0SkH1jtUrwsMdLr4CMw2bXRcH2wTh1cLlsVx_Y0lHUkUp7VYN9CzomL750MnQY_hjKSztTR1J8iZ-3JePJhtV4LIQNkaOh-Li1f1jtxmFyL7mb05pJ6CFKug",
    "expires_in": 3600,
    "token_type": "Bearer",
    "refresh_token": "18e3f0984546c7e8a4fd6de5dd13edfd12ea83b59cc4f09ab0009ca9cd7442d2"
}
```
获取的access_token数据可以在[https://jwt.io/]解码出来,access_token里放的数据尽量不要是重要的数据。