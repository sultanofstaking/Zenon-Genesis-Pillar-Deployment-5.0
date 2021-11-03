# Zenon-Testnet-Pillar-Deployment 5.0
## WARNING: I created this guide as an experiment for those setting up a pillar on 5.0 The steps below are my own and not endorsed by the Zenon team. This is being done in a very agile way, MVP of an experiment I expect our cross-functional community will participate and provide feedback so we can continuously improve. Please use the issue feature for fixes here. If you need to reach me 1:1 DM me on TG @SultanOfStaking - Try at your own risk. 

Pillar Node requirements
Hardware, CPU >= 4 cores, RAM >= 4 GB, Storage >= 40 GB free space, >100Mbps network dedicated bandwidth
Software, Linux distros e.g. Ubuntu 20.04 LTS/Debian 11, Recommended NTP configuration*, Recommended Watchdog service*
(*) Included if the setup is performed using the znn-controller

## Pillar Install (fresh install on new VPS)
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

Make files executable

`chmod +x znnd`

`chmod +x znn-cli`

`chmod +x znn-controller`

## If you are installing 5.0 as an upgrade reset your wallet, if not proceed to Enable RPC
Reset your wallet (this will delete all files and folders from the Zenon data folder, including any created wallets, so ensure you have a backup)

`./znn-cli reset`

Enable RPC

`./znn-cli enableRPC`

Start snnd

`./znn-cli start znnd`

# Deploy Pillar or Sentinel

`./znn-controller`

## If you found helpful no need to donate, but delegation to SultanOfStaking pillar would be appreciated https://explorer.znn.space/pillar/z1qpgdtn89u9365jr7ltdxu29fy52pnzwe4fl7zc

## If you are getting errors in your logs go here https://github.com/sultanofstaking/Zenon-Testnet-Node-Tips
