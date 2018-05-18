# 下载可执行文件

## 环境
*网络*： 独立IP地址  
*防火墙*：  开放39007、55027端口，分别用于p2p连接和rpc服务

## 下载（TODO）
- **ubunto & mac**
```
wget xxxx
tar -zxvf xxxxx.tar.gz
cp xxxx/bin/node /usr/bin/
```
- **windows**
```
set SEELE_PATH=xxxxx
set PATH=%PATH%;%SEELE_PATH%/build
```

## 配置
**下载测试网配置**：
```
git clone https://github.com/webbergao1/TNet
```
**配置 seele节点**：`config/nodeConfig.json`（详细见： https://github.com/seeleteam/go-seele ）

| 配置项 | 说明 |
| ----------- | --------- |
| Name  | 节点名字  |
|  StaticNodes  | 静态节点地址，默认为测试网节点  |
|  RPCAddr  | JSON-RPC端口，默认`55027` |
|  NetworkID  | 网络ID，填写测试网ID: `2`  |

**配置 monitor-api节点**：`config/app.conf` （详细见： https://github.com/seeleteam/monitor-api ）

| 配置项 | 说明 |
| ----------- | --------- |
| app_name  | 节点名字，在monitor监控页中显示 |
| RPCURL  | 本节点RPC链接地址，端口填写 `nodeConfig.json`中`RPCAddr`监听的地址，默认55027

## 启动
- **ubuntu & mac**  
```
node start -c nodeConfig.json
monitor-api
```
- **windows**  
```
node.exe start -c nodeConfig.json
monitor-api.exe
```

## seele-monitor 网站查看节点
访问seele-monitor网站：https://seelemonitor.io