# Download source code and compile
```
Git clone https://github.com/seeleteam/go-seele
```

## Environment
- **ubunto & mac**  
*Compile*:go development environment  
*Network*: Standalone IP address  
*Firewall*: Open ports 39007, 55027 for p2p connections and rpc services respectively  
- **windows**  
*Compile*: Go development environment, gcc tool (http://tdm-gcc.tdragon.net/download)  
*Network*: Standalone IP address  
*Firewall*: Open ports 39007, 55027 for p2p connections and rpc services respectively  

## Compile seele node
- **ubuntu & mac**
```
cd go-seeleå
Make all
cp build/node /usr/bin/
```
- **windows**
```
cd go-seele
buildall.bat
set PATH=%PATH%;%SEELE_PATH%/build
```

## Configure seele node
**Download Test Network Configuration**:
```
git clone https://github.com/webbergao1/TNet
```
**Modify configuration file**: `config/nodeConfig.json`

| Configuration Items | Description |
| ----------- | --------- |
| Name | Node Name |
| StaticNodes | test network default static node address |
| RPCAddr | JSON-RPC port, default `55027` |
| NetworkID | Network ID, filled: `2` |


## Start seele node
- **ubuntu & mac**
```
node start -c ./config/nodeConfig.json
```
- **windows**
```
node.exe start -c ./config/nodeConfig.json
```

## build moniotor-api
**Download and compile**
```
git clone https://github.com/seeleteam/monitor-api.git
cd monitor-api
go build
```

**Set environment variables**

- **ubuntu & mac**
            
```
cp build/monitor-api /usr/bin/
```

- **windows**

```
set PATH=%PATH%;%SEELE_PATH%/build
```


## Configure the moniotor-api

Modify the configuration file: `config/app.conf` (details: https://github.com/seeleteam/monitor-api)


| Configuration Items | Description |
| ----------- | --------- |
| App_name | node name, displayed on the monitor monitor page |
| RPCURL | This node's RPC link address, the port to fill in the `RPCAddr` listener address in `nodeConfig.json`, default 55027



## Start moniotor-api

- **ubuntu & mac**

```
monitor-api
```

- **windows**

```
monitor-api.exe
```

## seele-monitor site view node
Visit the seele-monitor website: https://seelemonitor.io