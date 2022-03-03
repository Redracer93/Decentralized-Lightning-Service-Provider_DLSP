# Decentralized Lightning Service Provider, DLSP
<br/>
<p align="center">
<a href="https://plenny.link" target="_blank">
<img src="https://user-images.githubusercontent.com/66779466/129766031-1d8eafda-b16e-483f-8897-53f78ccfd3b7.png" width="100" alt="Plenny logo">
</a>
</p>
<br/>

### Manual for lightning nodes to configure Lightning Oracles and Liquidity Makers
<br/>

## 1 Introduction

Plenny DLSP (Decentralized Lightning Service Provider) refers to the multifunctional open-source software for providing the decentralized lightning services of the Plenny Dapp and the Decentralized Oracle Network (DON) in order to process transaction data off-chain. This add-on module for lightning nodes supports both, Lightning Oracles and Liquidity Makers.

Lightning Oracles and Liquidity Makers download the same open-source software to operate as Plenny DLSPs. This specifically designed add-on module supports the computation of data off-chain for the provision of services over the DON and the capacity market on the Dapp. For integration, participants install an executable application on their lightning node. Depending on the configuration of the environment variables of the operating system, the service level and user type are recognized when connecting with Plenny. Participating in the DON to operate as an oracle validator is permission-less, as is the participation in the capacity market to operate as a Liquidity Maker. Any lightning node can run a Plenny DLSP. 

Participating lightning nodes operating as Plenny DLSP improve economics for potential fee income in Satoshi (sat) while earning additional income in Plenny (PL2) over DeFi. Operating as a Plenny DLSP involves the use of both, sat and PL2.

### 1.1 Lightning Oracle

Simply put, Lightning Oracles validate and observe payment channels activity. This component ensures connectivity and liquidity when lightning nodes interact with the Bitcoin Lightning Network and Plenny. In the broadest sense, these specific oracles work like lighthouses highlighting transaction data of payment channels allowing Plenny to safely navigate through the ecosystem across chains.  As for data protection and privacy, this is ensured between the participants on a P2P basis.

### 1.2 Liquidity Maker

Liquidity Makers (LM) act as DLSPs providing non-custodial inbound capacity. This role enables lightning nodes to participate in the capacity market while acting independently on the LN. LMs earn royalties for licensing transaction data services via payment communication channels on the one hand, and receive rewards from Plenny on the other. Rewards are given for operating lightning nodes, providing channel capacity to other lightning nodes, and for participating in the network. In the process, LMs transact with LTs directly using both, sat and PL2. Participating in the capacity market and operating as an LM is permission-less. Liquidity Makers utilize a specifically designed add-on module that supports processing data off-chain. This feature enables Lightning Nodes to participate in Plenny's capacity market as so-called DLSP and at the same time to operate independently via the LN. For integration, lightning nodes install an executable application to run the pre-configured software on their device. Any lightning node can download the open-source software and connect. Participating in the capacity market and operating as an LM is permission-less.

## 2 Plenny DLSP Architecture Diagram

![image](https://user-images.githubusercontent.com/66779466/156386547-18aed706-c834-4afe-b611-9c7b06aec372.png)


## 3 Prerequisite For - DLSP

The following prerequisites and requirements must be satisfied in order to install and run a DLSP successfully. The service will not proceed/run until all prerequisites are set up.

	1. Bitcoin Daemon Node (BTC)
		For more details: https://github.com/bitcoin/bitcoin
	2. Lightning Network Daemon (LND)
		For more details: https://github.com/lightningnetwork/lnd
	3. Ethereum Blockchain
		You can use your own or report RPC providers like Alchemy or Infura.
		For more details: https://docs.alchemy.com/alchemy/ or https://infura.io/docs
	4. SSL certificate (Self-signed/Trusted)
		We recommend to use a CA-signed certificate. However, a self-signed certificate will do just fine.
		To generate a self-signed certificate, run the following commands in your shell.
			#openssl genrsa -out key.pem
			#openssl req -new -key key.pem -out csr.pem
			#openssl x509 -req -days 9999 -in csr.pem -signkey key.pem -out cert.pem
		You need to update your pem files in server/certificates location.

## 4 Installing, configuring, and running DLSP

We provide binary files for installing the DLSP on Windows and Linux operating systems.

You can download the latest source release for Windows and Linux from here: https://github.com/PlennyPL2/Decentralized-Lightning-Service-Provider_DLSP/releases/

### 4.1 Installation Steps

	1. Download the latest source release with respect to your Operating System from here: https://github.com/PlennyPL2/Decentralized-Lightning-Service-Provider_DLSP/releases/
	2. Unzip the source file.
	3. Configure the .env file with your required parameters, which are explained in the next section.
	4. Upload your ssl certificates into server/certificates location
	5. Run "npm install"
	6. Execute the DLSP binary.

### 4.2  ETH_Wallet Settings

The ETH_Wallet that is used from the DLSP should NOT be used for any other transactions (e.g on DEXes or other Dapps) to avoid nonce errors.

### 4.3  Port number configuration of DLSP

You can provide the following settings.

	PORT=<Your_Port_Numer>
	
Example:

	PORT=3001
	
The default port number for the DLSP application is 3001. If you want to run multiple instances of DLSP, change the port number and start the application one by one.

### 4.4  Configuration of the DLSP environment file

The default environment variable file named “.env” which is placed in the project directory. The following syntax rule applied to the .env file.
- VAR=VAL
- Line beginning with “#” are processed as comments and ignored.
- Blank Lines are ignored.

In DLSP, configuration settings are divided into Four sections.


#### 4.4.1 Bitcoin Node configuration

The environment variables listed below are used to configure your Bitcoin node.

	BTC_HOST=<Your_Bitcoin_Host_Address>
	BTC_PORT=<Your_Bitcoin_node_RPCPort>
	BTC_USERNAME=<Your_Bitcoin_node_Username>
	BTC_PASSWORD=<Your_Bitcoin_node_Password>
	BTC_VERSION=<Your_Bitcoin_daemon_Version>
	BTC_NETWORK=<Your_Bitcoin_daemon_Network>
	
Example:

	BTC_HOST=192.168.0.1
	BTC_PORT=8332
	BTC_USERNAME=bitcoinrpc
	BTC_PASSWORD=mystrongpassword
	BTC_VERSION=0.21.0
	BTC_NETWORK=mainnet
	
#### 4.4.2 Ethereum RPC and Wallet configuration

The environment variables listed below are used to configure your Ethereum blockchain access point.

	LOCAL_RPC_URL= <your_Ethereum_remote_RPC_endpoint>
	SOCKET_RPC_URL=<Your_Ethereum_remote_RPC_WebSocket_endpoint>
	ETH_PRIV_KEY=<Your_Ethereum_Wallet_Private_Key_to_Address>
	
Example:

	LOCAL_RPC_URL=https://arb-rinkeby.g.alchemy.com/v2/xxxx
	SOCKET_RPC_URL=wss://arb-rinkeby.g.alchemy.com/v2/xxxx
	ETH_PRIV_KEY=4xxxx
	
NB: Your Ethereum private key must match with the account that you are using on the 
Plenny Dapp.
NB: The ETH_Wallet that is used from the DLSP should NOT be used for any other transactions (e.g on DEXes or other Dapps) to avoid nonce errors.

#### 4.4.3  LND Node configuration

The environment variables listed below are used to configure your LND node.

	LND_ADMIN_MACAROON_HEX=<HEX_Value_of_admin_macaroon>
	LND_TLS_CERT_HEX=<HEX_Value_of_TLS_certificate>
	LND_WALLET_PASS=<Your_LND_Wallet_Password>
	LND_HOST_PORT=<Your_LND_RPC_Port_Number>
	
NB: You can find your HEX value using the following command.

	xxd -p -c2000 admin.macaroon
	xxd -p -c2000 tls.cert
	
Example:

	LND_ADMIN_MACAROON_HEX=02010a108c7f2646a692c3d592f3c31b30a108c7f2646a692c3d592f3c31b3
	LND_TLS_CERT_HEX=2d2d2d20a4d4949434954430a4d49494349544354430a4d494943454430a4d4949454430a4d4949434
	LND_WALLET_PASS=mylndpassword
	LND_HOST_PORT=192.168.0.1:10009
	
#### 4.4.4  Configuration for restarting the Application

The environment variable listed below are used to restart the DLSP application. Restart option is provided, so the user can set the interval on how many seconds/minutes/hours the PlennyDLSP application should be restarted - Just in case the application has stopped working due to some issue.

	ALLOW_AUTO_RESTART=true/false
	RESTART_INTERVAL_SECONDS=Your_restart_interval_seconds
	AVERAGE_DAILY_BLOCK_COUNT=Your_average_daily_block_count
	
Example:

  	ALLOW_AUTO_RESTART=true
  	RESTART_INTERVAL_SECONDS=3600
  	AVERAGE_DAILY_BLOCK_COUNT=6500
	
### 4.5  Running DLSP

**Windows:**

Execute the PlennyDLSP.exe file and this will up and run a DLSP service.

**Linux:**

Before running the DLSP binary, you must export the .env environment variables. You can use the script below.

	export $(grep -v '^#' .env | xargs)
	
_First way to execute the binary_

	./PlennyDLSP
	
_Second way to execute the binary_

Fill in the fields in the run.sh file, and run the following command in your shell:

	./run.sh
	
## 5 Firewall Settings

To ensure high security, we ask that you open HTTPS 443 and Lightning Network Daemon (lnd) port 9735 to the public internet. For reference firewall settings, please see our DLSP simple architecture diagram.

## 6 Secure DLSP endpoint with HTTPS

DLSP application is reachable over HTTPS for secure communication. If you don't have an SSL certificate installed for the DLSP application, you'll have to use HTTP to access it. As a result, all standard web browsers will reject this access and classify it as "unsafe,". Moreover, Plenny Dapp will receive an error and respond accordingly. This issue is classified as "Mixed Content Warnings" over the web browser.

Make sure your endpoint for the DLSP is accessible through HTTPS to avoid this issue. You can use commercial or free SSL certificates. The SSL configurations listed below can be used:

- Dockerised solution using docker-compose [nginx server with Let’s Encrypt] https://letsencrypt.org/
- Cloud load balancer with Cloud provider's SSL [For cloud-hosted Decentralized Oracle Network]
- Using a Proxy webserver [Examples : HAProxy, Nginx]
https://www.haproxy.org/ ; https://www.nginx.com/ 

## 7 Claiming Lightning Node

Here are the steps describe how to claim a Lightning node on your Dapp:

**Step1: Plenny Dapp Lightning Node Page**

Go to dplenny.crypto/#/verify-lightning-nodes

Click "Claim Lightning Node"

![image](https://user-images.githubusercontent.com/66779466/156413259-dc9c1314-da94-40e7-b699-50a0ad61292f.png)

**Step2: Claim your Lightning Node**

Insert Your Lightning Node Public Key

Select Validator Lightning Node from the table below

Click “Add” and confirm the transaction (Ethereum wallet)

![image](https://user-images.githubusercontent.com/66779466/156413396-fd2a3908-5bbf-4bac-8e6f-e941dc005cdd.png)


**Step3: Verify your Lightning Node**

You should open a channel with the given channel capacity to the given node on the Lightning Network.

Click "Add Channel"

![image](https://user-images.githubusercontent.com/66779466/156419627-2e0fef8f-a9ab-4f16-b7dc-4f961a5ce5fd.png)

**Step4:  Add Channel**

You should insert your Channel Bitcoin Transaction ID and Channel Output Index.

Click "Apply" and confirm the transaction (Ethereum wallet)

![image](https://user-images.githubusercontent.com/66779466/156557661-7c538219-fe8a-4d21-99ce-a160c048451b.png)

The Channel Point is the combination of the Channel Bitcoin Transaction ID and the Channel Output Index and generated automatically from the Dapp.

For Step4 : How to find the Channel Output Index

![image](https://user-images.githubusercontent.com/66779466/156557799-b4dfa6ed-acc5-4a45-977a-f1d1ac55c068.png)

## 8 Launch the Lightning Oracle and/or Liquidity Maker on the Dapp

When the DLSP is configured and running you have to connect it with the Dapp itself. Therefore go to dplenny.crypto, login with your in section 4.4.2 configured Ethereum Wallet.

Afterwards go to dplenny.crypto/#/verify-lightning-nodes and claim your in section 4.4.3 configured Lightning Node. 

Once your Lightning Node is verified you can move on with the following steps. 

![image](https://user-images.githubusercontent.com/66779466/156557996-36e60007-b524-42cc-9fbc-ab3e6177ffed.png)

### 8.1 Launch Lightning Oracle

	1. Go to dplenny.crypto/#/lightning-oracle 
	2. Stake the Oracle Threshold in PL2 on your Staking Balance. If you don’t have any PL2, buy first.
	
![image](https://user-images.githubusercontent.com/66779466/156558106-25486b93-db6a-4968-8381-f504b8072b64.png)

	3. Click on “Launch Oracle”
	4. Add the details and save.
	Oracle Name = Give your Oracle a Name. This way you will be shown to other users.
	Lightning Node Public Key = Select your Lightning Node. Your node will only appear if you have verified it already.
	Lightning Node Host and Port = The public Node IP address
	Oracle Service URL = Your secure DLSP endpoint (https)

Example:

![image](https://user-images.githubusercontent.com/66779466/156558232-c6928331-58dc-47e1-96f2-fe2d4cefaacf.png)

### 8.2 Launch Liquidity Maker

	1. Go to dplenny.crypto/#/lightning-ocean
	2. Click on “Become Liquidity Maker”
	3. Set up the Liquidity Maker
	Liquidity Maker = Give your Maker a Name. This way you will be shown to other users.
	Service URL = Your secure DLSP endpoint (https)
	Public Key = Select your Lightning Node. Your node will only appear if you have verified it already.
	Allocated Node Liquidity = Maximum amount of Bitcoins (in Satoshi), which you can provide to Liquidity Takers.
	Price = The price you would like to get from a Liquidity Taker per Satoshi in PL2. 

Example:

![image](https://user-images.githubusercontent.com/66779466/156558389-70d758e8-343d-4a1c-8d61-05308cafcc47.png)



