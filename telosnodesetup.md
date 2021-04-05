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

### Mainnet

#### genesis.json

#### config.ini


