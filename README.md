## Masternode Setup - Step by step guide
 

Requirements: 	

1.) VPS for example on vultr or AWS on Amazon Services or Digital Ocean or Contabo

2.) for 1 Masternode you need a wallet with 5000 Sagiso Coins (1 coin for the fees)


 
## start in the wallet 
in wallet: Open Settings and  Debug console: 

```bash
createmasternodekey
```

<table>
<tr><td>example</td></tr>
<tr><td>7e5vjoZnh8Rnntt6wxxFU1LqPpXwXmBuzBrZetpsKUuvkpwVLCF</td></tr>
</table>

```bash
getnewaddress "MN1"  
```

<table>
<tr><td>example</td></tr>
<tr><td>SSm3URMZFTrwMnM39MKTBhwKaFR69mxCxw</td></tr>
</table>

# Send exact 5000 Coins to the address (confirmation need: 15) 


## Installation: for Security use SSH on your vps!!

Setup start with security on vps in putty (firewall)

```bash
sudo ufw allow 5600
```
```bash
sudo ufw allow 80
```
```bash
sudo ufw allow 5599
```
```bash
sudo ufw enable
```
You will be prompted with "Yes or no". type y and press enter

```bash
sudo ufw default deny
```

start install the requirements on VPS:

```bash
sudo apt-get update
```
```bash
sudo apt-get upgrade -y
```
```bash
sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils python3 libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev -y
```
```bash
sudo apt-get install libminiupnpc-dev libzmq3-dev libprotobuf-dev protobuf-compiler unzip software-properties-common -y
```
```bash
sudo add-apt-repository ppa:bitcoin/bitcoin
```
You will be prompted with "Enter". press enter

```bash
sudo apt-get update
```

download the wallet-client, tx and daemon file

```bash
sudo wget https://github.com/Sagiso/sagiso/releases/download/1000/sagiso-1.0.0-Linux.zip 
```


```bash
unzip sagiso-1.0.0-Linux.zip
```
```bash
sudo chmod +x sagisod
```
```bash
sudo chmod +x sagiso-tx
```
```bash
sudo chmod +x sagiso-cli
```
```bash
sudo mv sagisod sagiso-cli sagiso-tx /usr/bin/
```
```bash
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y
```
```bash
mkdir $HOME/.sagiso
```
```bash
nano $HOME/.sagiso/sagiso.conf
```

copy this with your details in th conf. file (choose only another good password, you need your masternode genkey from wallet and the ip address of the vps server)
```bash
#----
rpcuser=rpc_chooseagoodusername
rpcpassword=chooseagoodpassword
rpcallowip=127.0.0.1

listen=1
server=1
daemon=1
maxconnections=64

masternode=1
masternodeprivkey=your-MASTERNODE-GENKEY-from-debugconsole
externalip=IP-address

#----
```
save this file by pressing CONTROL+O and press enter
close this file by pressing CONTROL+X

# start the sagiso node with

```bash
sagisod
```
if everything is fine: you get an output: sagiso server starting




### back in your wallet
 
go to debug console

```bash
getmasternodeoutputs
```
<table>
<tr><td>example</td></tr>
 <tr><td>{</td></tr>
<tr><td>    "txhash": "c8ab8aa43d50cae6bf2b89b09f124bd83beaec00537884be8ec6585d1922", </td></tr>
<tr><td>     "outputidx": 1 {</td></tr>
<tr><td>   }</td></tr>
</table>


# Configure masternode.conf file (look at the example in file), reopen wallet and start masternode in debug console

<table>
<tr><td>example for masternode in masternode.conf file </td></tr>
<tr><td>mn1 IP_OF_THE_SERVER:5599 MASTERNODE_GENKEY TX_HASH TX_OUTPUTS</td></tr>
<tr><td>mn1 123.12.15.14:5599 7e5vjoZnh8Rnntt6wxxFU1LqPpXwXmBuzBrZetpsKUuvkpwVLCF c8ab8aa43d50cae6bf2b89b09f124bd83beaec00537884be8bae6585d1922 1</td></tr>
</table>

save file, reopen wallet and start in debug console !

```bash
startmasternode alias false MN1
```
