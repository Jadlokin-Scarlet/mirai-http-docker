# Mirai 镜像打包 模板
把shell运行的mirai迁移到docker中的一种打包方式，可以根据本模板为自己的mirai设计打包脚本

可以选择改造本模板或直接迁移已有的shell mirai项目

请自备qsign，修改KFCFactory.json和替换android_phone.json，要用的协议版本为ANDROID_PHONE 8.9.63

## 改造本模板
1. clone源码
```
git clone https://github.com/Jadlokin-Scarlet/mirai-http-docker
```
2. 改造模板

2.1 将要装的插件的jar放到plugins里。（例如/plugins/mirai-api-http-v2.3.1.mirai.jar）

2.2 将配置文件放到config里。(例如/config/net.mamoe.mirai-api-http/setting.yml)

2.3 修改AutoLogin.yml将QQbot的账号密码填进去

2.4 如果遇到设备验证问题无法登陆的话，把device.json放到/bots/{botQQ}/device.json，该文件获取方法请参考社区最新解决方案(https://mirai.mamoe.net/topic/223)

3. 构建镜像
```
 docker build -f DockerFile -t mirai .
```
4. 运行镜像
```
docker run --name mirai -p 8080:8080 -it mirai
```
5. 登陆完毕后CTRL+P+Q切入后台运行

## 迁移shell mirai至docker步骤
1. clone源码
```
git clone https://github.com/Jadlokin-Scarlet/mirai
```
2. 把DockerFile移至mirai安装目录
3. 构建镜像
```
 docker build -f DockerFile -t mirai .
```
4. 停掉shell mirai
5. 运行镜像
```
docker run --name mirai -p {ip}:{ip} -it mirai
```
5. 登陆完毕后CTRL+P+Q切入后台运行
