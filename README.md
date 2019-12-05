#  HttpReports
### �򵥽��� 
HttpReports �� .Net Core ��Ŀ��һ��Web����������� WebAPI ��Ŀ�� API ������Ŀ��ͨ���м������ʽ���ɵ�������Ŀ��, ͨ��HttpReports�������ÿ�����Ա���ٵĴ��һ�� API ���ܷ����Ļ���������վ��

��Ҫ���� HttpReports �м�� �� HttpReports.Web ������Ŀ��  
HttpReports�� https://github.com/SpringLeee/HttpReports
HttpReports.Web ��Ŀ���� https://github.com/SpringLeee/HttpReportsWeb

### ���ʹ��

##### 1.���� HttpReports.Web
 ��github���� HttpReports.Web ��Ŀ����Ŀ��ַ��https://github.com/SpringLeee/HttpReportsWeb, Web��Ŀ��.Net Core MVC ��Ŀ��ʹ������ʵ�֡�
 
 ![](https://raw.githubusercontent.com/SpringLeee/HttpReportsWeb/master/HttpReports.Web/wwwroot/Content/img/git/a1.png)
 
 
 
 ������ɺ���VS�д򿪣�Ȼ��ԭNuGet���������ɺ����� appsettings.json 
#### appsettings.json
```
{
  "ConnectionStrings": {
    "HttpReports": "Max Pool Size = 512;server=.;uid=sa;pwd=123456;database=HttpReports;"
  }, 
  "HttpReportsConfig": {
    "DBType": "SqlServer",
    "UserName": "admin",
    "Password": "123456"
  }
}

``` 
��Ҫ������
HttpReports������һ�����õ������ַ�����
DBType�����ݿ����ͣ�֧��SqlServer��MySql;
UserName: Web��Ŀ�ĵ�¼����
Password: Web��Ŀ�ĵ�¼���룻

��������ʹ�õ���SqlServer ���ݿ⣬������Ҫ����һ�����õ����ݿ������ַ�����Ȼ���ֶ��������ݿ� HttpReports�� Web��Ŀ��������ݿ��Զ����� �������ڵ�һ�����е�ʱ��MockһЩ���ݣ�����ֱ��F5������Ŀ�� û������Ļ�����ֱ��������¼ҳ�棬�����û������� admin 123456����¼��Ӧ�ÿ��Կ��������ҳ�棬
 ![](https://raw.githubusercontent.com/SpringLeee/HttpReportsWeb/master/HttpReports.Web/wwwroot/Content/img/git/a3.png) 

���ǿ���Mock����Щ���ݣ�
 �������� auth,payment��sms ��������ڵ㣬����ڵ�Ķ������£�
 
�����ַ | ����ڵ�  | ˵�� 
-|-|-
https://www.abc.com/auth/api/user/login | auth  |
https://www.abc.com/log/api/user/login | log  |
https://www.abc.com/api/user/login | default  |  ���û��ǰ׺�Ļ�������default�ڵ�

��������Ŀ�ǵ���WebAPI��Ŀ����ô����ڵ�ֻ��һ�� default����������Ŀ�� GateWay ������Ŀ����ôWeb��Ŀ�Ϳ��Զ�ȡ���������ڵ㣬���� auth ��֤��payment֧���ȡ�


##### 2. ���ɵ���Ŀ

����Ҫɾ�� Web ��Ŀ��Mock���ݣ������ݿ� HttpReports���򿪱� RequestInfo,������ݣ�ִ��Sql
```
  Delete * From [HttpReports].[dbo].[RequestInfo]
```
###### �������ݿ������ַ���
HttpReports ���õ���API��Ŀ��������Ŀ������ʹ�� Ocelot������ĿΪ��.

���Ǵ�appsetting.json, �������ݿ������ַ�������Ҫ��Web��Ŀһ��

![](https://raw.githubusercontent.com/SpringLeee/HttpReportsWeb/master/HttpReports.Web/wwwroot/Content/img/git/a6.png)

###### Nuget����HttpReports

��װnuget�� **HttpReports** ����StartUp

��ConfigureServices ��������ӣ� 
```csharp
services.AddHttpReportsMiddlewire();
```
�����MySql���ݿ⣬����ӣ�
 ```csharp
 services.AddHttpReportsMiddlewire(options =>{ 
    options.DBType = DBType.MySql; 
 });
```

���뵽 Configure ���� ����Ҫ���� app.UseMVC() ���� app.UseOcelot().Wait() ��ǰ�棬Ҫ��Ȼ����Ч
```csharp
app.UseHttpReportsMiddlewire();
```

ȫ��������Ժ����ǾͿ����� Web ��Ŀ�п��� API��Ŀ�����з�����
























 
 


 






















