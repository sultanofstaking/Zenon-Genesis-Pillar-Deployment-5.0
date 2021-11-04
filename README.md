# Zenon-Testnet-Pillar-Deployment 5.0
## WARNING: I created this guide as an experiment for those setting up a pillar on 5.0 The steps below are my own and not endorsed by the Zenon team. This is being done in a very agile way, MVP of an experiment I expect our cross-functional community will participate and provide feedback so we can continuously improve. Please use the issue feature for fixes here. If you need to reach me 1:1 DM me on TG @SultanOfStaking - Try at your own risk. 

## A few notes to start...
1. Treat technical, security, and wallet address strategy like it will carry over into alphanet (because it may)
2. Install the bundle from root as default data paths are set up that way
3. I am using Digital Ocean for testnet. Feel free to use my referral code for a $100 credit https://m.do.co/c/ab6f82b1c45f

## Pillar Node requirements

Hardware, CPU >= 4 cores, RAM >= 4 GB, Storage >= 40 GB free space, >100Mbps network dedicated bandwidth
Software, Linux distros e.g. Ubuntu 20.04 LTS/Debian 11, Recommended NTP configuration*, Recommended Watchdog service*
(*) Included if the setup is performed using the znn-controller

You will also need ZNN and QSR to spawn your pillar. If you are spawning a genesis pillar you will need 150k tQSR in the address you are planning to use as the controller.

## Pillar Install (fresh install on new VPS)
Start from root - if you are not sure enter the line below

`sudo su - root`

Install prereqs

`sudo apt install unzip`

`sudo apt install wget`

`sudo apt install gnupg`

Download bundle

`cd ~ && wget https://testnet.znn.space/downloads/v5.0.0/znn-public-incentivized-testnet-bundle-linux-amd64.zip?v=5.0.0`

Check testnet Quickstart https://testnet.znn.space/#!quickstart.md on how to verify bundle

Extract package

`unzip znn-public-incentivized-testnet-bundle-linux-amd64.zip?v=5.0.0`

Ensure all was extracted ok

`ls -lah`

You should see znn-cli, znnd, znn-controller, and corresponding argon2 and powlinks libraries

## If you are installing 5.0 as an upgrade from 4.0 reset your wallet, if not proceed to Enable RPC
Reset your wallet (this will delete all files and folders from the Zenon data folder, including any created wallets, so ensure you have a backup)

`./znn-cli reset`

Enable RPC

`./znn-cli enableRPC`

Start znnd

`./znn-cli start znnd`

# Deploy Pillar or Sentinel

`./znn-controller`

Select 1 to deploy the pillar, this will spit out a producer address (save this as you will need it in syrius). From here continue to register the pillar in syrius. Insert the address from the step above in the producer address section. You will also need to select reward distribution percentages. This can be adjusted later so dont overthink it.

Note: If you want to collect rewards in another address in syrius simply select "update pillar" on the pillar tab and imput the address.

## If you found helpful no need to donate, but delegation to SultanOfStaking pillar would be appreciated https://explorer.znn.space/pillar/z1qpgdtn89u9365jr7ltdxu29fy52pnzwe4fl7zc

## If you want to pull logs to diagnose errors go here https://github.com/sultanofstaking/Zenon-Testnet-Node-Tips
