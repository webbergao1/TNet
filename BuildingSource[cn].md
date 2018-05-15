
## 通过源码编译
下载go-seele源码: https://github.com/seeleteam/go-seele
### ubuntu & mac
#### 环境
	go 开发环境
	网络: 独立IP地址
	防火墙: 开放39007、55027端口，分别用于p2p连接和rpc服务

### 编译
执行 `make all`

### 配置
下载本工程里的 `nodeConfig.json`, json格式的配置文件，拷贝到go-seele/build文件夹下，并配置关键信息

| 配置项 | 说明 |
| ----------- | --------- |
| Name  | 节点名字  |
|  StaticNodes  | 静态节点地址，请填写我们提供的测试节点<s>**`XXX`**</s>  |
|  RPCAddr  | 端口默认**`55027`**，monitor监控服务使用，如更改需在monitor相应配置文件修改连接端口 |
|  NetworkID  | 网络ID，填写 **`1`**  |

### 启动节点
进入`build`文件夹执行 `node start -c <configfile>`
例如`./node start -c nodeConfig.json`

### 启动监控服务
- 下载监控服务可执行文件，地址 <s> https://xx.xx.com/13456 </s>，可通过wget命令下载
<s>`wget https://xx.xx.com/13456` </s>
- 将本工程里的 `monitorConfig.conf` 拷贝到监控服务可执行文件同目录
- 配置关键项

| 配置项 | 说明 |
| ----------- | --------- |
| app_name  | 节点名字，在监控浏览器中显示  |
| RPCURL  | 连接节点的地址，端口填写 `nodeConfig.json`中的 `RPCAddr`，默认55027


