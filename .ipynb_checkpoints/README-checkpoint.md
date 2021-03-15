# Philnet Blockchain Network

## Network Details
I created a local blockchain called "philnet" using puppeth, and created 2 nodes called "philnode1" and "philnode2" using geth.  See below for specific details

![puppeth_config_philnet](screenshots/puppeth_config_philnet.png)
![geth_node_creation_philnet](screenshots/geth_node_creation.png)

local blockchain network name: philnet
Chain/network ID: 247
philnode1 pw: philmill
Public address of the key:   0xeC2d302eDdbEA1C47872b30C873df9985939d1a1
Path of the secret key file: philnode1\keystore\UTC--2021-03-15T00-05-54.692180100Z--ec2d302eddbea1c47872b30c873df9985939d1a1

enode of philnode1: enode://34fcb376016928d8181aa8aa096fc6664f64e48119010c8ae1b1b3206ee3cae9284ee04b9501f731910e3cbbce029df20f8feaff6cbaf45193fbbfa050095341@127.0.0.1:30303

Philnode2 pw: philmill
Public address of the key:   0x2aCB4dfBA264E6E7c611B97BFfB02a20ec0EBc45
Path of the secret key file: philnode2\keystore\UTC--2021-03-15T00-06-22.255298600Z--2acb4dfba264e6e7c611b97bffb02a20ec0ebc45

## How to run Philnet

Navigate into your blockchain-tools directory which has the libraries for blockchain, i.e. geth, puppeth etc.

Run the following code to begin mining on philnode1: ./geth --datadir philnode1 --unlock "0xeC2d302eDdbEA1C47872b30C873df9985939d1a1" --mine --rpc --allow-insecure-unlock

Run the following code to mine on philnode2: ./geth --datadir philnode2 --unlock "0x2aCB4dfBA264E6E7c611B97BFfB02a20ec0EBc45" --port30304 --rpc --bootnodes "enode://34fcb376016928d8181aa8aa096fc6664f64e48119010c8ae1b1b3206ee3cae9284ee04b9501f731910e3cbbce029df20f8feaff6cbaf45193fbbfa050095341@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock

See below of readme for the Geth Flags Dictionary

## Connecting to MyCrypto

Once the local blockchain network was created and was able to mine ETH, you can connect it to MyCrypto to send transactions. In order to do so, you must create a custom network, in this example I created a "philnet" custom network to connect to my local blockchain(See below for screenshot of setup). Once you are connected via the custom network, you can send transactions between the nodes. I sent 500 ETH to philnode2 using the address and private key of node 2 that was created in geth when we initialized the nodes (see below for transaction).
![mycrypto_custom_node_setup](screenshots/mycrypto_custom_node_setup.png)

![transaction](screenshots/transaction.png)

## Geth Flags Dictionary

ACCOUNT OPTIONS:
  --unlock value                      Comma separated list of accounts to unlock
  --password value                    Password file to use for non-interactive password input
  --signer value                      External signer (url or path to ipc file)
  --allow-insecure-unlock             Allow insecure account unlocking when account-related RPCs are exposed by http

API AND CONSOLE OPTIONS:
  --ipcdisable                        Disable the IPC-RPC server
  --ipcpath value                     Filename for IPC socket/pipe within the datadir (explicit paths escape it)
  --rpc                               Enable the HTTP-RPC server
  --rpcaddr value                     HTTP-RPC server listening interface (default: "localhost")
  --rpcport value                     HTTP-RPC server listening port (default: 8545)
  --rpcapi value                      API's offered over the HTTP-RPC interface
  --rpc.gascap value                  Sets a cap on gas that can be used in eth_call/estimateGas (default: 0)
  --rpccorsdomain value               Comma separated list of domains from which to accept cross origin requests (browser enforced)
  --rpcvhosts value                   Comma separated list of virtual hostnames from which to accept requests (server enforced). Accepts '*' wildcard. (default: "localhost")
  --ws                                Enable the WS-RPC server
  --wsaddr value                      WS-RPC server listening interface (default: "localhost")
  --wsport value                      WS-RPC server listening port (default: 8546)
  --wsapi value                       API's offered over the WS-RPC interface
  --wsorigins value                   Origins from which to accept websockets requests
  --graphql                           Enable the GraphQL server
  --graphql.addr value                GraphQL server listening interface (default: "localhost")
  --graphql.port value                GraphQL server listening port (default: 8547)
  --graphql.corsdomain value          Comma separated list of domains from which to accept cross origin requests (browser enforced)
  --graphql.vhosts value              Comma separated list of virtual hostnames from which to accept requests (server enforced). Accepts '*' wildcard. (default: "localhost")
  --jspath loadScript                 JavaScript root path for loadScript (default: ".")
  --exec value                        Execute JavaScript statement
  --preload value                     Comma separated list of JavaScript files to preload into the console

NETWORKING OPTIONS:
  --bootnodes value                   Comma separated enode URLs for P2P discovery bootstrap (set v4+v5 instead for light servers)
  --bootnodesv4 value                 Comma separated enode URLs for P2P v4 discovery bootstrap (light server, full nodes)
  --bootnodesv5 value                 Comma separated enode URLs for P2P v5 discovery bootstrap (light server, light nodes)
  --port value                        Network listening port (default: 30303)
  --maxpeers value                    Maximum number of network peers (network disabled if set to 0) (default: 50)
  --maxpendpeers value                Maximum number of pending connection attempts (defaults used if set to 0) (default: 0)
  --nat value                         NAT port mapping mechanism (any|none|upnp|pmp|extip:<IP>) (default: "any")
  --nodiscover                        Disables the peer discovery mechanism (manual peer addition)
  --v5disc                            Enables the experimental RLPx V5 (Topic Discovery) mechanism
  --netrestrict value                 Restricts network communication to the given IP networks (CIDR masks)
  --nodekey value                     P2P node key file
  --nodekeyhex value                  P2P node key as hex (for testing)

MINER OPTIONS:
  --mine                              Enable mining
  --miner.threads value               Number of CPU threads to use for mining (default: 0)
  --miner.notify value                Comma separated HTTP URL list to notify of new work packages
  --miner.gasprice value              Minimum gas price for mining a transaction (default: 1000000000)
  --miner.gastarget value             Target gas floor for mined blocks (default: 8000000)
  --miner.gaslimit value              Target gas ceiling for mined blocks (default: 8000000)
  --miner.etherbase value             Public address for block mining rewards (default = first account) (default: "0")
  --miner.extradata value             Block extra data set by the miner (default = client version)
  --miner.recommit value              Time interval to recreate the block being mined (default: 3s)
  --miner.noverify                    Disable remote sealing verification