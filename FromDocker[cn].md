## 通过下载Docker镜像

通过Docker镜像启动节点并加入测试网络<br>
我们提供go-seele镜像和monitor-api镜像，并在docker-compose.yml文件里启动。

### 环境
	安装Docker
	安装Docker compose
	防火墙: 开放39007、55027端口，分别用于p2p连接和rpc服务

### 配置go-seele镜像
修改本工程里的 `docker-compose/node_config/nodeconfig.json`

| 配置项 | 说明 |
| ----------- | --------- |
| Name  | 节点名字  |
|  StaticNodes  | 静态节点地址，请填写我们提供的测试节点<s>**`XXX`**</s>  |
|  RPCAddr  | 端口默认**`55027`**，monitor监控服务使用，如更改需在monitor相应配置文件修改连接端口 |
|  NetworkID  | 网络ID，填写 **`1`**  |

### 配置monitor-api镜像
修改本工程里的 `docker-compose/monitor-api-config/app1.conf`

| 配置项 | 说明 |
| ----------- | --------- |
| app_name  | 节点名字，在监控浏览器中显示  |
| RPCURL  | 填入连接节点的IP地址，端口默认55027  <br> 如有修改填入docker-compose中映射的端口|

### 配置Docker-compose
修改本工程的 `docker-compose/docker-compose.yml`

我们默认启动go-seele和monitor-api镜像

##### go-seele镜像:

| 配置项 | 说明 |
| ----------- | --------- |
| volumes  | 挂载本地`docker-compose/node_config`文件夹到镜像的/go-seele/config文件夹  |
| command  | 启动节点 `node start -c /go-seele/config/nodeconfig.json`。|
| ports  | < rpc port >:55027 给app1.conf的`RPCURL`使用<br> < http port >:65027 <br> < p2p port >:39007|
##### monitor-api镜像:

| 配置项 | 说明 |
| ----------- | --------- |
| volumes  | 挂载本地`docker-compose/monitor-api-config/app1.conf`文件到镜像的/monitor-api/app.conf文件  |

### 启动Docker镜像
`run docker-compose run`
