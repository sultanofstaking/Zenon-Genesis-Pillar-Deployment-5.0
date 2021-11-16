# Zenon-Genesis-Pillar-Deployment 5.0

## WARNING: I created this guide as an experiment for those setting up a genesis pillar on 5.0 The steps below are my own and not endorsed by the Zenon team. This is being done in a very agile way, MVP of an experiment I expect our cross-functional community will participate and provide feedback so we can continuously improve. Please use the issue feature for fixes here. If you need to reach me 1:1 DM me on TG @SultanOfStaking - Try at your own risk. 

## Pillar Node requirements

Hardware, CPU >= 4 cores, RAM >= 4 GB, Storage >= 40 GB free space, >100Mbps network dedicated bandwidth
Software, Linux distros e.g. Ubuntu 20.04 LTS/Debian 11 (recommend ubuntu 20.04)

Also Recommended NTP configuration*, Recommended Watchdog service* **These are Included if the setup is performed using the znn-controller**

You will need 15k tZNN and 150k tQSR in the syrius address you are using to spawn your pillar. You can get this from the faucet on TG (https://t.me/znnfaucet_bot). If you are short tQSR because you used it for plasma then ask for someone to send you more in the main channel.

## A few notes before you start...
1. Treat technical, security, and wallet address strategy like it will carry over into alphanet
2. Install the bundle from root as default data paths are set up that way
3. Ensure you have a swp file from your legacy wallet that took place after the snapshot (if you are not sure, download a new swp file)
4. Ensure any address you are interacting with in syrius has plasma fused otherwise you risk needing to wait for plasma to be generated.

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

Enable RPC

`./znn-cli enableRPC`

Start znnd

`./znn-cli start znnd`

# Deploy Pillar or Sentinel

`./znn-controller`

Select 1 to deploy the pillar, this will spit out a producer address (save this as you will need it in syrius). From here continue to register the pillar in syrius via the pillar tab > spawn pillar. Be sure to select genesis pillar. Syruis will ask you for your swp file then show you the pillar address(es) eligible to select as genesis pillars. Insert the producer address from the VPS. You will also need to select reward distribution percentages. This can be adjusted later so dont overthink it.

Again, use an address strategy you are comfortable with in alphanet e.g., perhaps a transaction address, rewards address, and controller address. 

After you have set your genesis pillar up go to the testnet explorer and check if it is producing momentums. If not, go here to diagnose errors go here https://github.com/sultanofstaking/Zenon-Testnet-Node-Tips

## If you found helpful no need to donate, but delegation to SultanOfStaking pillar would be appreciated https://explorer.znn.space/pillar/z1qpgdtn89u9365jr7ltdxu29fy52pnzwe4fl7zc 
