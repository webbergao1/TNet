# Download executable file

## Environment
- **ubuntu & mac**  
*Network*: Standalone IP address  
*Firewall*: Open ports 39007, 55027 for p2p connections and rpc services respectively  
- **windows**  
*Network*: Standalone IP address  
*Firewall*: Open ports 39007, 55027 for p2p connections and rpc services respectively  

## Download（TODO）
- **ubuntu & mac**
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

## Configuration

**Download test network configuration**:
```
git clone https://github.com/webbergao1/TNet
```
**Modify node configuration file**: `config/nodeConfig.json` ( details https://github.com/seeleteam/go-seele ）

| Configuration Items | Description |
| ----------- | --------- |
| Name | Node Name |
| StaticNodes | test network default static node address |
| RPCAddr | JSON-RPC port, default `55027` |
| NetworkID | Network ID, filled: `2` |

**Modify monitor-api configuration file**: `config/app.conf` (details: https://github.com/seeleteam/monitor-api )


| Configuration Items | Description |
| ----------- | --------- |
| App_name | node name, displayed on the monitor monitor page |
| RPCURL | This node's RPC link address, the port to fill in the `RPCAddr` listener address in `nodeConfig.json`, default 55027

## Start 
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

## seele-monitor site view node
Visit the seele-monitor website: https://seelemonitor.io