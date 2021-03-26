# How to setup a validator node on Telos
* A validator needs to know it's role & fulfill the requirements.

## What is the role of a Telos Validator
* They are a core component of Telos network built on EOSIO protocol.
* They provide stability, reliability, security and extensive infrastructure coverage for Telos network.
* Contribute to Telos developerment toolkits, so as to get noticed by the voters & stay in BP list eligibile for incentives (in TLOS tokens).

### Telos Validator Requirements
* 

## What is a Telos validator node

## Types of nodes

### API

### History API

### Seed

### Producer
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

## Configuration Files

### Mainnet

#### genesis.json

#### config.ini


