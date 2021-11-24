---
title: "NFT IDEA to Customers with a Product built-in"
date: 2021-10-19T11:58:09-07:00
draft: true
---



## Problem

An award given should be proveable even if that physical representation of the award was lost, yet if the physical object is lost did the award every really exist.


## Solution NFT

Having a way to represent ownership to digital content on the web is a very powerful feature. The decentralized nature of the blockchain or what I like to call very slow peer-to-peer databases gives that implicit trust that a smart contract was minted and cannot be changed, thus can represent ownership.

## What are NFT

ERC-721, a non fugebal token. ERC-721 has a tokenid and each token is unqiue and each token represents a unique asset. Has on-chain and off-chain attributes. on-chain is desired since the attributes are proven by the cryptographic function to pull it on the chain.


## References

[Chainlink D&D Character](https://blog.chain.link/build-deploy-and-sell-your-own-dynamic-nft/)



### How do you create an NFT

Goto

1. https://opensea.io/
2. Create an account by connecting your wallet. There are a few I suggest [walletconnect](https://walletconnect.com/).
3. Click the hamburger icon and click connect wallet. Click Wallet Connect
4. Click Trust (I use trust for the iphone)
5. Complete your profile by valledating your opensea account
6. opensea wallet walletconnect to iphone wallet: `0xd4f15be249bb9432a3cf870df0b781ee9eefa445`
7. create a collection
8. add image to a collection
9. upload your image
10. add meta data
11. Get a [contract](https://etherscan.io/address/0x495f947276749ce646f68ac8c248420045cb7b5e) url




### Developer tools to interact with ETH

* 
* [Infura](https://infura.io/) makes developer tools 
* [Golang Eth](https://ethereum.org/en/developers/docs/programming-languages/golang/) list of resources for go engineers
* [HardHat](https://hardhat.org/) A recommended JS developer framework for building smart contracts
* [Truffle](https://www.trufflesuite.com/) The oldest framework, that has set a lot of standards and precendent. Many of the projects on github are probably truffle projects
* [Brownie](https://github.com/eth-brownie/brownie) This is a python framework, depends on Web3.py and is the highest used
* [Go-Ethereum](https://github.com/ethereum/go-ethereum) Official Golang implementation of the Ethereum protocol. GETH is the main ETH CLI client. Geth is the main entry point into the ETH network exposing endpoints on top HTTP, WEBSOCKETS, or IPC transports.
* [GETH Tutorial](https://medium.com/coinmonks/creating-and-exploring-a-private-ethereum-blockchain-using-geth-d71afc5cdcf9) This is a tutorial on how to set up GETH
* [Go Smart Contract Deploy](https://goethereumbook.org/smart-contract-deploy/) This shows how to deploy a smart contract.




### Environmental Setup for Development

We are going to use brownie and Solidity to code our nft. Additionally we are going to use the contracts by openzeplin


```
$ mkdir nft-idea && cd nft-idea
$ brownie init 
```

Create a .env file and add infuria token and wallet token to your environment

```

export WEB3_INFURA_PROJECT_ID= # allows rest api to eth network
export PRIVATE_KEY= #metamask private key so we can interact with the wallet
export ETHERSCAN_TOKEN= #support for verifing things show up on etherscan

```


Download IPFS
```
curl -O https://dist.ipfs.io/go-ipfs/v0.10.0/go-ipfs_v0.10.0_darwin-amd64.tar.gz
```

Run IPFS

```
ipfs deamon 
```


At this point we have the ability to write Solidity and run brownie to compile it and brownie can run a soon to be created deploy script for the contract.

THe following directory structure is made:
```
tests  # where we will put our integration and unit tests
scripts # location of the python code that browine will execute to deploy, mint, update metadata
reports # 
interfaces # interfaces for existing deployed contracts which are interacted with
contracts # this is where our Solidity code is located 
build #output of solc
```


### Writing the Contract


We are creating a nft factory to push out a certain token type. Within that contract we can then mint nfts. What we will do is create our own factory contract and mint the nft with that contract.

This is accomplished by a few steps
* create the brownie project defined above
* in contracts create a contract
* in the workspace directory add env settings and a brownie config to rewrite paths to github repos from python
* brownie compile


```
 brownie compile
Brownie v1.17.0 - Python development framework for Ethereum

Compiling contracts...
  Solc version: 0.6.6
  Optimizer: Enabled  Runs: 200
  EVM Version: Istanbul
Generating build data...
 - OpenZeppelin/openzeppelin-contracts@3.4.0/ERC165
 - OpenZeppelin/openzeppelin-contracts@3.4.0/IERC165
 - OpenZeppelin/openzeppelin-contracts@3.4.0/SafeMath
 - OpenZeppelin/openzeppelin-contracts@3.4.0/ERC721
 - OpenZeppelin/openzeppelin-contracts@3.4.0/IERC721
 - OpenZeppelin/openzeppelin-contracts@3.4.0/IERC721Enumerable
 - OpenZeppelin/openzeppelin-contracts@3.4.0/IERC721Metadata
 - OpenZeppelin/openzeppelin-contracts@3.4.0/IERC721Receiver
 - OpenZeppelin/openzeppelin-contracts@3.4.0/Address
 - OpenZeppelin/openzeppelin-contracts@3.4.0/Context
 - OpenZeppelin/openzeppelin-contracts@3.4.0/EnumerableMap
 - OpenZeppelin/openzeppelin-contracts@3.4.0/EnumerableSet
 - OpenZeppelin/openzeppelin-contracts@3.4.0/Strings
 - CompanyAward

The project has been compiled. Build artifacts saved at /Users/dathan/workspace/award-nft/build/contracts

~/workspace/award-nft (main) [minikube|]
$ 
```




### Tests

Unit tests are supported by brownie, as well as integration tests. Using the pytest package, define the test in tests/unit


### Gas

Gas is very interesting, the ability to esitimate is really variable since its based on the compute power of the code being executed.

* [What the net has to say](https://ethereum.stackexchange.com/questions/19665/how-to-calculate-transaction-fee)
* [another one](https://ethereum.stackexchange.com/questions/68662/how-to-determine-transaction-fees-using-web3-py)
* [web3.py](https://web3py.readthedocs.io/en/stable/web3.eth.html#web3.eth.Eth.getTransactionReceipt)
* web3.py read's the last block to get the gas estimate in some instances
 


### side goal
<details>
<summary></summary>
<p>
```
* mac book pro is [$3,700.00](https://www.apple.com/shop/buy-mac/macbook-pro/14-inch-space-gray-10-core-cpu-16-core-gpu-1tb#) 
* 2 mac displays [$14000.00](https://www.apple.com/shop/buy-mac/pro-display-xdr/nano-glass)
* anything my wife wants [$7000000+](https://foreveraward.com)
```
</p>
</details>

