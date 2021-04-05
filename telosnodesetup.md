# How to setup a validator node on Telos
* A validator needs to know it's role & fulfill the requirements.

## What is the role of a Telos Validator
* They are a core component of Telos network built on EOSIO protocol.
* Telos Validators play a key role in the operation of the network. 
* They provide stability, reliability, security and extensive infrastructure coverage for Telos network.
* Contribute to Telos developerment toolkits, so as to get noticed by the voters & stay in BP list eligibile for incentives (in TLOS tokens).
* Telos Validators verify transactions on the Telos networks by collecting transaction data and storing that information in blocks. 
* Once a block is prepared, validators broadcast the block to the network for verification.

### Telos Validator Requirements

## What is a Telos validator node
* In the Telos network, block production and block validation are performed by special nodes called "Telos validator node". Validator nodes are elected by Telos stakeholders. Each validator node runs an instance of an Telos node using the nodeos service. For this reason, validators that are on the active schedule to produce blocks are also called "active" or "producing" validator nodes.

## Types of nodes
* In the Telos blockchain network, you might find the slightly different naming of nodes, such as a API node, Producer node, History-API node, Seed node. All nodes keep updating an internal database by applying the transactions as they arrive in incoming blocks. The difference between the node types lies in the amount of history they keep track of, and in the functionality they provide.
* After proper EOS.IO core software release installed, each type node is implemented by the same executable, however, each node would need to set up different configurations to start the node. For example; although a block producing node can have full history, that would be a waste of resources. Block producing nodes should run with minimal plugins (i.e., only witness_plugin). Also, Block producing nodes should not have open network ports. We strongly recommend all node service providers to run and maintain their own nodes for reliability and security reasons.

### API
API nodes provide network services to client applications. They usually have account transaction histories accessible though API calls, but can vary in the amount of available history. 

### History API
History-API nodes are API nodes with a complete transaction history of all accounts.

### Seed
* A seed node is a special node that allows the incorporation of new nodes to the network and maintains the strength of the network at all times, by allowing them to synchronize and obtain a copy of the data from the blockchain, replicating it and adding resistance and security to it.
* Seed nodes are nodes that accept incoming P2P connections. They are the first nodes contacted by a freshly started node. In that sense they serve as an entry point into the network. Once a node has entered the network it will receive additional node addresses from its peers, so all nodes can connect to each other. A seed node can also be an API node. The Telos core software i.e. EOS.IO comes with a preconfigured list of seed nodes for easy bootstrapping.
* The seed nodes are used only to locate or find complete nodes that are running the Telos Blockchain client.
* So, when a new node wants to gain access to the network, it must connect with a seed node, which is a Telos client that is always active and has a static IP address. This client operates as a gateway to the Telos network, being one of the first connections that Telos clients make at the beginning.
* Thus, seed nodes play an important role within the network, operating from highly trusted servers. Allowing new clients to connect to the Telos network automatically and without the need for manual intervention by a user. Although it may be the case that some of these nodes can become dishonest, causing a negative impact within the network. So it is not recommended to place trust in a single seed node.

### Producer
* A producer node is a node run by a Block Producer (BP). Each producer node (active/top-21 only) validates all blocks and transactions it receives. The nodes of elected (active/top-21 only) producers take turns in bundling new transactions into blocks and broadcasting them to the network.
* Producer nodes generally runs in two modes using `nodeos` EOSIO component:

#### Producing Node
* __Producing Nodes__ are configured for block production.
* They connect to the peer-to-peer network and actively produce new blocks.
* Loose transactions are also validated and relayed.
* On mainnet, they only produce blocks if their assigned block producer is part of an active schedule. 

#### Non-Producing Node
* __Non-Producing__ Nodes connect to the peer-to-peer network but do not actively produce new blocks.
* They are useful for acting as proxy nodes, relaying API calls, validating transactions, broadcasting information to other nodes, etc. 
* They are also useful for monitoring the blockchain state.

## Installation Methods
* EOSIO currently supports the following operating systems:
	- Amazon Linux 2
	- CentOS 7
	- Ubuntu 16.04
	- Ubuntu 18.04
	- MacOS 10.14 (Mojave)

> NOTE: If you are new to EOSIO, it is recommended that you install the EOSIO Prebuilt Binaries. If you are an advanced developer, a block producer, or no binaries are available for your platform, you may need to Build EOSIO from source depending on your OS.

### Ubuntu package method
```console
$ wget https://github.com/eosio/eos/releases/download/v2.0.11/eosio_2.0.11-1-ubuntu-18.04_amd64.deb
$ sudo apt install ./eosio_2.0.11-1-ubuntu-18.04_amd64.deb
```

### Compile source code method
1. Clone the `EOSIO/EOS` repository from Github like this:
```console
$ git clone https://github.com/EOSIO/eos.git --recursive` [NOT NEEDED, if already cloned]
```

> NOTE: The step-1 is not needed, if the repository is already cloned. Directly, start from step-2.

1. Go to the `eos` folder 
```console
$ cd eos
```
1. pull the repository with required released version 
```console
$ git pull https://github.com/EOSIO/eos.git v2.0.11`
```
1. update the submodules
```console
$ git submodule update --init --recursive`
```
1. Go to required version
```console
$ git checkout tags/v2.0.11`
```

## run Nodeos

### A. Producing mode

### B. Non-Producing mode

## Configuration Files

### Testnet

#### genesis.json
```
{
 "initial_key": "EOS52vfcN43YHHU8Akh7VyfBdnDiMg15dPTELosWG9SR86ssBoU1T",
 "initial_configuration": {
   "max_transaction_delay": 3888000,
   "min_transaction_cpu_usage": 100,
   "net_usage_leeway": 500,
   "context_free_discount_net_usage_den": 100,
   "max_transaction_net_usage": 524288,
   "context_free_discount_net_usage_num": 20,
   "max_transaction_lifetime": 3600,
   "deferred_trx_expiration_window": 600,
   "max_authority_depth": 6,
   "max_transaction_cpu_usage": 5000000,
   "max_block_net_usage": 1048576,
   "target_block_net_usage_pct": 1000,
   "max_generated_transaction_count": 16,
   "max_inline_action_size": 4096,
   "target_block_cpu_usage_pct": 1000,
   "base_per_transaction_net_usage": 12,
   "max_block_cpu_usage": 50000000,
   "max_inline_action_depth": 4
 },
 "initial_timestamp": "2018-12-12T10:29:00.000"
}
```

#### producer config.ini
```
chain-state-db-size-mb = 1024000
reversible-blocks-db-size-mb = 1024000

http-server-address = 0.0.0.0:8888
#https-server-address = 0.0.0.0:443

access-control-allow-origin = *
access-control-max-age = 1
http-validate-host = false
access-control-allow-headers = Origin, X-Requested-With, Content-Type, Accept

filter-on = *
filter-out = nebulatpstps::
filter-out = eosio:onblock:

max-clients = 250
connection-cleanup-period = 120
#network-version-match = 1
sync-fetch-span = 10000

verbose-http-errors = true

plugin = eosio::chain_plugin
plugin = eosio::chain_api_plugin
plugin = eosio::http_plugin
plugin = eosio::producer_plugin

wasm-runtime = eos-vm-jit
chain-threads = 4
cpu-effort-percent = 20
last-block-cpu-effort-percent = 10
last-block-time-offset-us = -300000

p2p-peer-address=<See peer list at telos.net>

producer-name = <your account name>

signature-provider = <your public key here>
```

#### api config.ini
```
chain-state-db-size-mb = 1024000
reversible-blocks-db-size-mb = 1024000

http-server-address = 0.0.0.0:8888
#https-server-address = 0.0.0.0:443

access-control-allow-origin = *
access-control-max-age = 1
http-validate-host = false
access-control-allow-headers = Origin, X-Requested-With, Content-Type, Accept

filter-on = *
filter-out = nebulatpstps::
filter-out = eosio:onblock:

max-clients = 250
connection-cleanup-period = 120
#network-version-match = 1
sync-fetch-span = 10000

verbose-http-errors = true

plugin = eosio::chain_plugin
plugin = eosio::chain_api_plugin
plugin = eosio::http_plugin

wasm-runtime = eos-vm-jit
chain-threads = 4
cpu-effort-percent = 20
last-block-cpu-effort-percent = 10
last-block-time-offset-us = -300000

p2p-peer-address=<See peer list at telos.net>
```

### Mainnet

#### genesis.json
```
{
 "initial_key": "EOS52vfcN43YHHU8Akh7VyfBdnDiMg15dPTELosWG9SR86ssBoU1T",
 "initial_configuration": {
   "max_transaction_delay": 3888000,
   "min_transaction_cpu_usage": 100,
   "net_usage_leeway": 500,
   "context_free_discount_net_usage_den": 100,
   "max_transaction_net_usage": 524288,
   "context_free_discount_net_usage_num": 20,
   "max_transaction_lifetime": 3600,
   "deferred_trx_expiration_window": 600,
   "max_authority_depth": 6,
   "max_transaction_cpu_usage": 5000000,
   "max_block_net_usage": 1048576,
   "target_block_net_usage_pct": 1000,
   "max_generated_transaction_count": 16,
   "max_inline_action_size": 4096,
   "target_block_cpu_usage_pct": 1000,
   "base_per_transaction_net_usage": 12,
   "max_block_cpu_usage": 50000000,
   "max_inline_action_depth": 4
 },
 "initial_timestamp": "2018-12-12T10:29:00.000"
}
```

#### producer config.ini
```
chain-state-db-size-mb = 1024000
reversible-blocks-db-size-mb = 1024000

http-server-address = 0.0.0.0:8888
#https-server-address = 0.0.0.0:443

access-control-allow-origin = *
access-control-max-age = 1
http-validate-host = false
access-control-allow-headers = Origin, X-Requested-With, Content-Type, Accept

filter-on = *
filter-out = nebulatpstps::
filter-out = eosio:onblock:

max-clients = 250
connection-cleanup-period = 120
#network-version-match = 1
sync-fetch-span = 10000

verbose-http-errors = true

plugin = eosio::chain_plugin
plugin = eosio::chain_api_plugin
plugin = eosio::http_plugin
plugin = eosio::producer_plugin

wasm-runtime = eos-vm-jit
chain-threads = 4
cpu-effort-percent = 20
last-block-cpu-effort-percent = 10
last-block-time-offset-us = -300000

p2p-peer-address=<See peer list at telos.net>

producer-name = <your account name>

signature-provider = <your public key here>
```

#### api config.ini
```
chain-state-db-size-mb = 1024000
reversible-blocks-db-size-mb = 1024000

http-server-address = 0.0.0.0:8888
#https-server-address = 0.0.0.0:443

access-control-allow-origin = *
access-control-max-age = 1
http-validate-host = false
access-control-allow-headers = Origin, X-Requested-With, Content-Type, Accept

filter-on = *
filter-out = nebulatpstps::
filter-out = eosio:onblock:

max-clients = 250
connection-cleanup-period = 120
#network-version-match = 1
sync-fetch-span = 10000

verbose-http-errors = true

plugin = eosio::chain_plugin
plugin = eosio::chain_api_plugin
plugin = eosio::http_plugin

wasm-runtime = eos-vm-jit
chain-threads = 4
cpu-effort-percent = 20
last-block-cpu-effort-percent = 10
last-block-time-offset-us = -300000

p2p-peer-address=<See peer list at telos.net>
```
