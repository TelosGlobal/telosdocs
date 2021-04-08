# How to setup a validator node on Telos
* A validator needs to know it's role & fulfill the requirements.
* Having more validators is healthier and better for the Telos ecosystem, especially validators that are committed to transparency, and being in a state of giving continuous contribution.
* Validators are a core component of Telos network built on EOSIO protocol.
* Below is the guide to get a node up and running as a Validator on Telos.

## What is the role of a Telos Validator
* Validators are decentralized entities that govern the Telos blockchain. Validators will produce the blocks of the Telos blockchain.
* Telos Validators play a key role in the operation of the network.
* They provide stability, reliability, security and extensive infrastructure coverage for Telos network.
* Contribute to Telos developerment toolkits, so as to get noticed by the voters & stay in BP list eligibile for incentives (in TLOS tokens).
* Telos Validators verify transactions on the Telos networks by collecting transaction data and storing that information in blocks. 
* Once a block is prepared, validators broadcast the block to the network for verification.
* Validators will earn block rewards in the form of TLOS tokens produced by token inflation.
* Validators are responsible for Telos infrastructure growth, community support and education, and financial support for development of Telos DApps.

### Telos Validator Requirements
* <u>__A Mission__</u> — what are you going to provide to the world as a Validator? How will you spend your TLOS? Why should people vote for you?
* <u>__Unique EOS producer account__</u> — This should not resemble the name of any current Telos Validator Candidates. You can view all of the current Validators and Validator Candidates here: https://telos.bloks.io/
* <u>__A few servers running nodeos__</u> — virtual machines or even a desktop with a lot of RAM would be ok to start off. Some Block Producers are running on desktop hardware (i7 or i9 chips). You just need to provide the RAM that is required by Telos Mainnet and it increases at 1 KB/block currently. It is ~ 12.56 GB at the time of writing this.
* <u>__Website__</u> — your website should have a `bp.json` ([example](https://www.alohaeos.com/bp.json)) at it's root, and links to an ownership disclosure ([example](https://www.alohaeos.com/ownership)), and a code of conduct ([example](https://www.alohaeos.com/conduct))).
* <u>__Producer account creation for rewards__</u> — Create a unique Telos Account that will be the name of your Validator. Telos Accounts are 12 characters long. For more, visit here: 
	- [Telos account creator](https://telos-account-creator.com/)
	- [FREE Telos account via Sqrl Wallet](https://telosuk.io/how-to-create-a-free-telos-account/)

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
`nodeos` generally runs in 2 modes:

### A. Producing/Active mode
`Producing Validator Nodes` are configured for block production. They connect to the peer-to-peer (p2p) network and actively produce new blocks. Loose transactions are also validated and relayed. On mainnet, Producing Validator Nodes only produce blocks if their assigned block producer is part of an active schedule.

> NOTE: <u>System contracts required</u> - 
> These instructions assume you want to launch a producing validator node on a network with system contracts loaded. These instructions will not work on a default development node using native functionality, or one without system contracts loaded.

#### Goal
This section describes how to set up a producing node within the EOSIO network. A producing node, as its name implies, is a node that is configured to produce blocks in an EOSIO based blockchain. This functionality if provided through the producer_plugin as well as other Nodeos Plugins.

##### nodeos plugins
* Plugins extend the core functionality implemented in `nodeos`. Some plugins are mandatory, such as `chain_plugin`, `net_plugin`, and `producer_plugin`, which reflect the modular design of `nodeos`. The other plugins are optional as they provide nice to have features, but non-essential for the nodes operation.
* The list of specific plugins are as follows:
	- `blockvault_client_plugin`
	- `chain_api_plugin`
	- `chain_plugin`
	- `db_size_api_plugin`
	- `history_api_plugin`
	- `history_plugin`
	- `http_client_plugin`
	- `http_plugin`
	- `login_plugin`
	- `net_api_plugin`
	- `net_plugin`
	- `producer_plugin`
	- `state_history_plugin`
	- `trace_api_plugin`
	- `txn_test_gen_plugin`

> <u>Nodeos is modular</u>: Plugins add incremental functionality to `nodeos`. Unlike runtime plugins, nodeos plugins are built at compile-time.

#### Pre-requisites
* Install the [EOSIO software](#installation-methods) before starting this section.
* It is assumed that `nodeos`, `cleos`, and `keosd` are accessible through the path. If you built EOSIO using shell scripts, make sure to run the Install Script.
* Know how to pass Nodeos options to enable or disable functionality.

#### Steps
Please follow the steps below to set up a producing node:

1. [Local Wallet]()
1. [Create your `bp.json` for your Telos validator]()
1. [Register your account as a producing validator](#1-register-your-account-as-a-producing-validator)
1. [Set Producer Name]()
1. [Set the Producer's signature-provider]()
1. [Define a peers list]()
1. [Load the Required Plugins]()

##### 1. Local Wallet
###### a. Create Telos Wallet locally. Record the password and keep secure.
```console
cleos wallet create -n <wallet_name> --to-console
<!-- OR -->
cleos wallet create -n <wallet_name> --file <filename_with_extension>
```

###### b. Unlock EOS Wallet. Paste your wallet password
```console
cleos wallet unlock -n <wallet_name> --password <wallet_password>
```

###### c. Account creation:
* M-1: Use services like [Telos account creator](https://telos-account-creator.com/) or [FREE Telos account via Sqrl Wallet](https://telosuk.io/how-to-create-a-free-telos-account/) to create your account.
* M-2: Using CLI

```console 
#todo
<!-- cleos -u http://api.main.alohaeos.com system newaccount — stake-net "4.0000 TLOS" — stake-cpu "4.0000 EOS" — buy-ram-kbytes 8 accountname newaccountname <owner-publickey> <active-publickey> -->

cleos -u http://api.main.alohaeos.com system newaccount — stake-net "4.0000 TLOS" — stake-cpu "4.0000 EOS" — buy-ram-kbytes 8 alohaeosprod newaccountname <owner-publickey> <active-publickey>
```

###### d. Load new account private key into your wallet
```console
cleos wallet import -n <wallet_name> <privkey>
```

##### 2. Create your `bp.json` for your Telos validator
This will be used by voting portals and websites to identify validators. The `bp.json` contains location info for your Block Validator, nodes, and also contains other identifiable information such as your Block Producer public key.

For instance, http://yourwebsite.com/bp.json When you register your validator, the URL field should be filled with http://yourwebsite.com. Do not put the `bp.json` file in the URL.

For instance, for Aloha, the `bp.json` is located at https://www.alohaeos.com/bp.json, the URL to locate this will be https://www.alohaeos.com.

* [Template for the standard bp_info.json format for the EOS Mainnet.](https://github.com/eosrio/bp-info-standard)
* You can find most Validator's bp.json at their websites.
* Please conform to the [JSON format standard](https://www.w3schools.com/js/js_json_syntax.asp).
* Here is an excellent [JSON validator](https://jsonformatter.org/).

##### 3. Register your account as a producing validator
In order for your account to be eligible as a producing validator, you will need to register the account as a producing validator:
```console
<!-- cleos -u <api_endpoint> system regproducer <producer_account_name> <producer_signature_public_key> <producer_website> <producer-geo-location> -->
cleos -u http://api.main.alohaeos.com system regproducer alohaeosprod EOS87wJkSDXLDVVoJUaBYd4tjg8F8chMWY5nPo8Mb5F919TpbjJvz https://www.alohaeos.com Honolulu
```

> NOTE: separate key pair used only for signing blocks and can not perform any other operation.

> If you currently have your active key listed in your `config.ini` for signing blocks — you need to stop it and replace it with a separate Signature key

Just follow this in order to 

##### 4. Set Producer Name
Set the `validator_name` option in `config.ini` to your account, as follows:
```
# config.ini:

# ID of producer controlled by this node (e.g. inita; may specify multiple times) (eosio::producer_plugin)
producer-name = alohaeosprod
```

##### 5. Set the Producer's signature-provider
You will need to set the private key for your validator. The public key should have an authority for the validator account defined above.

### B. Non-Producing or Standby mode
`Non-Producing Validator Nodes` connect to the peer-to-peer (p2p) network but do not actively produce new blocks; they are useful for acting as proxy nodes, relaying API calls, validating transactions, broadcasting information to other nodes, etc. `Non-Producing Validator Nodes` are also useful for monitoring the blockchain state.



## Configuration Files

### Mainnet

#### genesis.json

#### config.ini


