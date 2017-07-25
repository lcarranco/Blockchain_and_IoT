# Blockchain_and_IoT
How to build a simple IoT device and connect it to the Ethereum blockchain

This IoT device is connected to the Ethereum blockchain and is used to open a door (in this case the door lock is represented by an LED) when the appropriate amount of funds are sent by a user on the blockchain. 

This is a simple example and requires a more rigorously-tested version in order to implement it in production but it demonstrates how an IoT device can be connected, controlled, and responded to in response to certain events on an Ethereum blockchain.z

## Mastering Blockchain
This idea came from the book by Imran Bashir *Mastering Blockchain*

## Setting up
When this project was initially taken on I assumed it was going to be a plug and play type of scenario. I was wrong. The reason is because I have an older model of the Raspberry Pi and I had to do a lot of research to find work arounds. This is mostly due to Ethereum clients being developed for the newer models Raspberry Pi 2 and Raspberry Pi 3. I have Raspberry Pi Model B. [Here is a handy guide](https://www.element14.com/community/community/raspberry-pi/blog/2016/11/21/how-to-identify-which-model-of-the-raspberry-pi-you-have) on how to identify which Raspberry Pi model you have.

After doing many hours of research I finally came across an excellent repo to install Ethereum on nearly every model of Raspberry Pi. [Link](https://github.com/EthEmbedded/Raspi-Eth-Install)
