# Blockchain_and_IoT
How to build a simple IoT device and connect it to the Ethereum blockchain

This IoT device is connected to the Ethereum blockchain and is used to open a door (in this case the door lock is represented by an LED) when the appropriate amount of funds are sent by a user on the blockchain. 

This is a simple example and requires a more rigorously-tested version in order to implement it in production but it demonstrates how an IoT device can be connected, controlled, and responded to in response to certain events on an Ethereum blockchain.z

This idea came from the book *Mastering Blockchain* by Imran Bashir.

## Setting up Raspberry Pi
When this project was initially taken on I assumed it was going to be a plug and play type of scenario. I was wrong. The reason is because I have an older model of the Raspberry Pi and I had to do a lot of research to find work arounds. This is mostly due to Ethereum clients being developed for the newer models Raspberry Pi 2 and Raspberry Pi 3. I have Raspberry Pi Model B. [Here is a handy guide](https://www.element14.com/community/community/raspberry-pi/blog/2016/11/21/how-to-identify-which-model-of-the-raspberry-pi-you-have) on how to identify which Raspberry Pi model you have.

After doing many hours of research I finally came across an excellent repo to install Ethereum on nearly every model of Raspberry Pi. [Link](https://github.com/EthEmbedded/Raspi-Eth-Install)

[Command Line Options](https://github.com/ethereum/go-ethereum/wiki/Command-Line-Options)

## First Boot
### Update Locale

Must be in root

Configure your default locale: `dpkg-reconfigure locales`

Configure your timezone: `dpkg-reconfigure tzdata`

[Link](https://github.com/debian-pi/raspbian-ua-netinst)

### Disable screen from turning off

\*Make sure you are logged into your created user account

[Link](https://raspberrypi.stackexchange.com/a/61080)

## Geth Account Creation
Created account: `./geth account new`

## MainNet
MainNet is the current live network of ethereum. The current version of MainNet is __Homestead__

## TestNet (Ropsten)
Used by developers or users as a test platform to test smart contrats and other blockchain-related proposals.

Connect to TestNet: `./geth --testnet`

## PrivateNet
Allows creation of an independent private network that can be used as a distributed ledger between participating entities and for the development and testing of smart contracts. Create an entirely new blockchain.

### Setting up PrivateNet
Need three components to create PrivateNet
1. Network ID
2. Genesis file
3. Data directory to store blockchain data\*

\*Data directory is not strictly required. If there is more than one blockchain active on the system, then data directory should be specified so that a separate directory is used for the new blockchain.

PrivateNet differs from MainNet and TestNet in that it uses its own unique genesis block and Network ID

On MainNet, geth knows about peers by default and connects automatically.

On PrivateNet, geth needs to be configured by specifying appropriate flags and configuration in order for it to be able to be discoverable by other peers or to discover other peers.

Should disable node discovery so that other nodes on the internet can not discover your private network and is truly private.

### Netword ID
Network ID can be any positive number except 1 and 3. 1 and 3 are already in use by MainNet and TestNet respectively.

Network ID 786 was chosen as an example in the book.

### Genesis file
The genesis file contains necessary fields required for a custom genesis block. This is the first block in the network and does not point to any previous block. The Ethereum protocal does rigorous checking to ensure that no other node on the internet can participate in the consensus mechanism, unless they have the same genesis block.

Here is a custom genesis file that was chosen as an example in the book. This file can be saved in a text file with the JSON extenstion.
```
{
    "nonce": "0x0000000000000042",
    "timestamp": "0x0",
    "parentHash":"0x0000000000000000000000000000000000000000000000000000000000000000",
    "extraData": "0x0",
    "gasLimit": "0x4c4b40",
    "difficulty": "0x400",
    "mixhash":"0x0000000000000000000000000000000000000000000000000000000000000000",
    "coinbase": "0x0000000000000000000000000000000000000000",
    "alloc": { }
}
```
Ether can be preallocated by specifying beneficiary addresses and the amount of Wei in `alloc`, but it is usually not necessary because being on the private network, either can be mined very quickly.
