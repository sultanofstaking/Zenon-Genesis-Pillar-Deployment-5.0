# Zenon-Genesis-Pillar-Deployment 5.0

**WARNING: I created this guide as an experiment for those setting up a pillar on alphanet. The steps below are my own and not endorsed by the Zenon team. This is being done in a very agile way, MVP of an experiment I expect our cross-functional community will participate and provide feedback so we can continuously improve. Please use the issue feature for fixes here. If you need to reach me 1:1 DM me on TG @SultanOfStaking - Try at your own risk.**

## Pillar Node requirements

Hardware, CPU >= 4 cores, RAM >= 4 GB, Storage >= 40 GB free space, >100Mbps network dedicated bandwidth
Software, Linux distros e.g. Ubuntu 20.04 LTS/Debian 11 (recommend ubuntu 20.04)

Also Recommended NTP configuration*, Recommended Watchdog service* **These are Included if the setup is performed using the znn-controller**

## A few notes before you start...
1. The requirements above are minimum requirements provided by the team. Block 27070 hung many pillars running at the minimum requirements without swap space. Because of this I would recommend you opt for a machine with at least 8GB ram and set up swap space. If you need help with setting up a swap space or your VPS in general feel free to leverage my guide here https://github.com/sultanofstaking/VPS-Set-Up-Tips/blob/main/README.md
2. You will need 15k ZNN and 150k QSR in the syrius address you are using to spawn your pillar if you had one of the original 136 pillars on the legacy network. Pillars registered after the 136 legacy pillars need an additional 10k QSR each. So pillar 137 needs 160k QSR, pillar 138 needs 170k QSR and so on.
3. Once registered funds are locked for 83 days. After 83 days a 7 day window opens where the pillar can be revoked. If you revoke your pillar you will receive the 15k ZNN but no QSR as they are burned upon pillar registration. At the end of the 7 day window the cycle repeats itself.
4. If you are registering a genesis / legacy pillar ensure you have a wallet.dat file from your legacy wallet that took place after the snapshot (if you are not sure, download a new .dat file)
5. Install the bundle from root as default data paths are set up that way
7. Ensure any address you are interacting with in syrius has plasma fused otherwise you risk needing to wait for plasma to be generated.

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

# Deploy Pillar 

`./znn-controller`

Select deploy pillar, this will spit out a producer address (save this as you will need it in syrius). From here continue to register the pillar in syrius via the pillar tab > spawn pillar. If you select genesis pillar Syruis will ask you for your wallet.dat file then show you the pillar address(es) eligible to select as genesis pillars. Insert the producer address from the VPS when prompted. You will also need to select reward distribution percentages. This can be adjusted later so dont overthink it.

After you have set your pillar up pull logs and ensure your pillar is inserting and producing momentums. To learn how to pull logs and to diagnose errors go here https://github.com/sultanofstaking/Zenon-Testnet-Node-Tips

## If you found helpful no need to donate, but delegation to SultanOfStaking pillar would be appreciated (although something tells me you will be delegating to your brand new pillar)
