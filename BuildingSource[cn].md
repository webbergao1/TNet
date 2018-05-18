# 下载源码编译
```
git clone https://github.com/seeleteam/go-seele
```

## 环境
- **ubunto & mac**  
*编译*：go开发环境  
*网络*： 独立IP地址  
*防火墙*：  开放39007、55027端口，分别用于p2p连接和rpc服务
- **windows**  
*编译*：go开发环境,    gcc工具（http://tdm-gcc.tdragon.net/download ）  
*网络*： 独立IP地址  
*防火墙*： 开放39007、55027端口，分别用于p2p连接和rpc服务

## 编译 seele node
- **ubuntu & mac**
```
cd go-seele
make all
cp build/node /usr/bin/
```
- **windows**
```
cd go-seele
buildall.bat
set PATH=%PATH%;%SEELE_PATH%/build
```

## 配置 seele node
**下载测试网配置**：
```
git clone https://github.com/webbergao1/TNet
```
**修改配置文件**：`config/nodeConfig.json`

| 配置项 | 说明 |
| ----------- | --------- |
| Name  | 节点名字  |
|  StaticNodes  | 静态节点地址，默认为测试网节点  |
|  RPCAddr  | JSON-RPC端口，默认`55027` |
|  NetworkID  | 网络ID，填写测试网ID: `2`  |


## 启动 seele node
- **ubuntu & mac**  
```
node start -c ./config/nodeConfig.json
```
- **windows**  
```
node.exe start -c ./config/nodeConfig.json
```

## 编译 moniotor-api
**下载并编译**
```
git clone https://github.com/seeleteam/monitor-api.git
cd monitor-api
go build
```

**设置环境变量**  

- **ubuntu & mac** 
            
```
cp build/monitor-api /usr/bin/
```

- **windows**  

```
set PATH=%PATH%;%SEELE_PATH%/build
```


## 配置 moniotor-api

修改配置文件：`config/app.conf` （详细见： https://github.com/seeleteam/monitor-api ）


| 配置项 | 说明 |
| ----------- | --------- |
| app_name  | 节点名字，在monitor监控页中显示 |
| RPCURL  | 本节点RPC链接地址，端口填写 `nodeConfig.json`中`RPCAddr`监听的地址，默认55027


## 启动 moniotor-api

- **ubuntu & mac**

```
monitor-api
```

- **windows**

```
monitor-api.exe
```

## seele-monitor网站查看节点
访问seele-monitor网站：https://seelemonitor.io