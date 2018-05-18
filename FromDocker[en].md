## Downloading Docker image

Starting a node with a docker image and joining the test network <br>
We provide go-seele image and monitor-api image, and the docker-compose.yml file to start.

### Environment
- Install Docker  
- Install Docker compose  
- Firewall: Open port 39007 and 55027 for p2p connection and rpc service respectively  
### Configure the go-seele image
Modify `docker-compose/node_config/nodeconfig.json` in this project ( details https://github.com/seeleteam/go-seele ）

| Configuration Items | Description |
| ----------- | --------- |
| Name | Node Name |
StaticNodes | Static Node Address, please fill out the test node address we provided<s>**`XXX`**</s> |
| RPCAddr | Port default `55027`, monitor service used | 
| NetworkID | Network ID, fill in **`2`** |

### Configure the monitor-api image
Modify `docker-compose/monitor-api-config/app1.conf` in this project ( details: https://github.com/seeleteam/monitor-api )

| Configuration Items | Description |
| ----------- | --------- |
| app_name | node name, displayed in the monitoring browser |
| RPCURL | Fill in the IP address of the connecting node, the default port is 55027 <br> Modify the port that is mapped in docker-compose |

### Configure Docker-compose
Modify `docker-compose/docker-compose.yml` in this project

We start the go-seele and monitor-api images by default

##### go-seele image:

| Configuration Items | Description |
| ----------- | --------- |
Volumes | Mount the local `docker-compose/node_config` folder to the image /go-seele/config folder |
| command | Start the node `node start -c /go-seele/config/nodeconfig.json`. |
| ports | < rpc port >: 55027 Used by the configuration item `RPCURL` in app1.conf <br> < http port >:65027 <br> < p2p port >:39007|
##### monitor-api image:

| Configuration Items | Description |
| ----------- | --------- |
Volumes | Mount the local `docker-compose/monitor-api-config/app1.conf` file to the mirrored /monitor-api/app.conf file |

### Start Docker Image

```
Docker-compose run
```

## seele-monitor Website View Node
Visit the seele-monitor website: https://seelemonitor.io