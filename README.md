# katchcoin blockchain

On this repository, a set of instructions is presented to setup a private blockchain network to record transactions using Ethereum "logic" in a new blockchain network named: katchcoin.

## Setting Up the katchcoin Network:

The katchcoin network consists of 2 nodes (a mining node and a transactional node). To setup the network and operate the network, follow the following steps:

step 1: Make sure that the following items are installed and running: (Mycrypto wallet[1] and blockchain genesis tools[2]). Ensure the blockchain genesis tool is Unzipped from the ethereum package and renamed as `Blockchain-Tools`

step 2: copy node5 and node6 from the repository Nodes folder into the `Blockchain-Tools` folder on C drive computer. Also, copy the Network `katchcoin.json` file (located in folder Blockchain_network folder) into the `Blockchain-Tools` folder on C drive.

step 3: Initiate each node. by typing the following command, node 5 is initialized:
```shell
./geth init katchcoin.json --datadir node5
``` 
Repeat the same command but change node5 with node6, to initialize the Transactional node (node6).

step 4: Run the mining node (node5), by typing the following command in the terminal: 
```shell
./geth --datadir node5 --unlock "<Public Address from Node5 Keystore>" --mine --rpc --allow-insecure-unlock
```
![node 5 running](Screenshots/run_node5.png)

Once the mining node is running, copy the enode path (this information is needed to run the transactional node)

![copy enode](Screenshots/enode_to_copy.png)

step 5: Run the Transactional node (node 6), by opening another terminal window and typing this command in the `Blockchain-Tools` folder:

```shell
./geth --datadir node6 --unlock "<Public Address from Node6 Keystore>" --mine --port 30304 --bootnodes enode://<Enode from Node5> --ipcdisable
```

The Transactional node must use a different port from the "mining" node, thus the port command 30304 must be specified to ensure that the port doesn't get reassigned.

## Configuring katchcoin network in MyCrypto wallet:

To be able to execute transactions, and while both nodes are running in their respective terminal windows, the crypto wallet needs to be configured with the `katchcoin` network. To configure the network in the wallet: open MyCrypto and create a custom node called: `katchcoin`, network name: `katchcoin`, with Chain ID `333`, and URL: `http://127.0.0.1:8545`. Refer to attached video for the configuration.

![configuring katchcoin in myCrypto](Screenshots/crypto_network_config.gif)


## Executing Transactions with katchcoin network:

<img src=Screenshots/balances_before_after.png width="400" align="right" />
Once the network is setup in the wallet and while the two nodes are running on their windows, the system is ready to operate.

To demonstrate that the katchcoin network is functional, a big transaction (50,000,000,000,000 ETH) was initiated from node 5 to node 6 with the objective of identify the balance change from the sender node (node5).

To complete the transaction, open the wallet using the the `Private Key` option and paste the following private key

 Alternatively, the private key can be obtained by opening wallet using `Keystore File` option and locating the keystore folder located inside the node5 folder. Once there, reveal the private keys for node 5 (this is required in order to authorize transactions).


![nodes running](Screenshots/nodes_running_transac.png)

Additionally, an image of both nodes mining (signalling) during the transaction process as well as a status screenshot `pending` confirms that the katchcoin network is processing the transaction.

<img src=Screenshots/status_pending.png width="350" align="left" />







## Resources:

For installation of MyCrypto Wallet and ethereum commands, refer to:

[1] https://download.mycrypto.com/

[2] https://geth.ethereum.org/


