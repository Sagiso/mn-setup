# Masternode Setup Guide - MANUALLY GUIDE

### Required:

1. enough SAGISO for Collateral 

2. Download Local Wallet for your operating system: : https://github.com/Sagiso/sagiso/releases

3. You will need also VPS with Ubuntu 18.04

**VPS WALLET:**

1. After you longin on your VPS , with this command you will download masternode-installer.   
`wget https://raw.githubusercontent.com/Sagiso/mn-setup/master/masternode-install.sh`  
 

2. With this command you will make masternode-install.sh executable:  

- Use this: <br>
`sudo chmod +x masternode-install.sh` <br>

3. Now install your masternode.  
`./masternode-install.sh`

4.  go to your **LOCAL WALLET:**
Open your wallet and wait until your wallet has downloaded the blockchain.

Go to “Tools”.
Click “Debug console”.
This is the console where you will execute all commands.

Create a new masternode private key.

```
createmasternodekey
```

Example output
```
7e4ZzZEkyNKtoegNCtmqnoHxNbAiWojBWuA7Fouehok4cRQSseB
```

Copy this to Linux and press Enter! 

5. Send the collateral

Show your collateral address.
```
getnewaddress "MN1"
```

Example output
```
SiYrUoeNACjU3o5ibv8WwoBR8Km4ZSkhX5
```
Transfer the required amount of sagiso coins to the “collateral address” that you created using the command “getnewaddress "MN1"”.

Wait until the transaction has the required masternode confirmations.

Go to “Tools”.
Click “Debug console”.
Enter the following command.
```
getmasternodeoutputs
```

Example output

```
[
  {
    "txhash": "2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c",
    "outputidx": 1
  }
]
```

Modify the following line in your masternode.conf file and paste it into:
```
MN1 VPSIP:5599 7e4ZzZEkyNKtoegNCtmqnoHxNbAiWojBWuA7Fouehok4cRQSseB 2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c 1
```
MN1 - Alias for your masternode.

VPSIP- External IP address of your VPS.

5599 - The port for Sagiso

7e4ZzZEkyNKtoegNCtmqnoHxNbAiWojBWuA7Fouehok4cRQSseB - Masternode private key from the command “createmasternodekey”.

2bcd3c84c84f87eaa86e4e56834c92927a07f9e18718810b92e0d0324456a67c - Value “txhash” from the command “getmasternodeoutputs”.

1 - Value “outputidx” from the command “getmasternodeoutputs”.


Save the file and close.

Close your wallet.

Restart your wallet! 
On Masternode tab in your wallet - Start the masternode! 

If you still facing any issues 
then join our <a href="https://discord.gg/mQgDHj8fwp"> Discord server</a> for support. 

We are happy to help you there! 
