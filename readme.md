## 反代性能对比测试


### Api发布运行 

* api编译发布
```bash
    cd ./Api/
    dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true
```

* api运行命令
```bash

    WebApplication1.exe --urls http://*:8081

```


### 反向代理

* yarp
```bash
    cd .\yarpTest\
    dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true
    yarpTest.exe --urls http://*:8082

```

* nginx
* caddy


### 测试工具
* 接口直连
```bash
    bombardier-windows-amd64.exe -c 1000 -d 30s -l http://127.0.0.1:8081/WeatherForecast
```

* yarp反向代理
```bash
    bombardier-windows-amd64.exe -c 1000 -d 30s -l http://127.0.0.1:8082/WeatherForecast
```
* nginx反向代理
```bash
    bombardier-windows-amd64.exe -c 1000 -d 30s -l http://127.0.0.1:80831/WeatherForecast
```
* caddy反向代理
```bash
    bombardier-windows-amd64.exe -c 1000 -d 30s -l http://127.0.0.1:8084/WeatherForecast
```
### 
![对比](.\compare.png)