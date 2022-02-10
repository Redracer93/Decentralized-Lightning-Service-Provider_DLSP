# Lightning_Oracle
<br/>
<p align="center">
<a href="https://plenny.link" target="_blank">
<img src="https://user-images.githubusercontent.com/66779466/129766031-1d8eafda-b16e-483f-8897-53f78ccfd3b7.png" width="100" alt="Plenny logo">
</a>
</p>
<br/>

## Overview
<br/>
Lightning Oracles serve as a chain link to connect lightning nodes to the Dapp. In the broadest sense, these proprietary oracles work like lighthouses highlighting key data of payment channels and allowing for navigation across chains. They record payment channel capacity while optionally providing data privacy.

Simply put, Lightning Oracles validate transaction data to ensure connectivity and liquidity when interacting with the Bitcoin Lightning Network and the Ethereum blockchain.

The token economy allows Lightning Oracles to earn fees for providing validation services. To incentivize early adopters, participating nodes earn higher rewards during the experimental phase in the beginnings of the Dapp. Once critical mass has been reached, rewards adjust proportionally. As a guiding principle, Lightning Oracles earn higher rewards than Plenny Whalers (PWs) who allocate cryptocurrency for Liquidity Mining. Lightning Oracles get higher rewards because they provide technical services for the lightning economy interconnected to the digital economy of the Dapp, and ensure the security of the DON, while PWs only hold token within the decentralized financial economy.

THIS IS PENDING for update. needs some input from BK

## A Simple Architecture Diagram

![image](https://user-images.githubusercontent.com/66779466/133470798-81f4ac72-feb0-4a63-aa64-70c32aed300e.png)


## Prerequisite For Lightning Oracle

The following prerequisites and requirements must be satisfied in order to install and run a Lightning Oracle successfully. The oracle service will not proceed/run until all prerequisites are set up.

      1. Bitcoin Daemon Node (BTC)
            For more details: https://github.com/bitcoin/bitcoin
      2. Lightning Network Daemon (LND)
            For more details:  https://github.com/
      3. Ethereum Blockchain
            You can use your own or report RPC providers like Alchemy or Infura.
            For more details: https://docs.alchemy.com/alchemy/ or https://infura.io/docs 
      4. SSL certificate (Self-signed/Trusted)
            We recommend to use a CA-signed certificate. However, a self-signed certificate will do just fine.
            To generate a self-signed certificate, run the following commands in your shell.
                  #openssl genrsa -out key.pem
	          #openssl req -new -key key.pem -out csr.pem
	          #openssl x509 -req -days 9999 -in csr.pem -signkey key.pem -out cert.pem
            You need to update your pem files in server/certificates location
                       
## Installing, configuring, and running the Lightning Oracle application

We provide binary files for installing the Lightning Oracle Service on Windows and Linux computers.
You can download the latest source release for Windows and Linux Operating System from here: https://github.com/PlennyPL2/Lightning_Oracle/releases

### Installation Steps

      1. Download the latest source release with respect to your Operating 
         System from here: https://github.com/PlennyPL2/Lightning_Oracle/releases 
      2. Unzip the source file.
      3. Configure the .env file with your required parameters.
      4. Upload your ssl certificates into server/certificates location
      5. Run "npm install"
      6. Execute the Lightning Oracle binary.
      
### ETH_Wallet Setting
The ETH_Wallet that is used from the DLSP should NOT be used for any other transactions (e.g on DEXes or other Dapps) to avoid nonce errors.

### Common Settings

The default environment variable file named .env which is placed in the project directory. The following syntax rule applied to the .env file.

* VAR=VAL
* Line beginning with “#” are processed as comments and ignored.
* Blank Lines are ignored.

In Lightning Oracle, configuration settings are divided into Five sections.


### Configuration for Lightning Oracle application:

You can provide the following settings.
      
      PORT=<Your_Port_Numer>

Example:

      PORT=3001
      
The default port number for Lightning Oracle is 3001. If you want to run multiple instances of Lighting Oracle, change the port number and start the application one by one.

### Configuration of Bitcoin Nodes

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
      
### Configuration of Ethereum blockchain

The environment variables listed below are used to configure your Ethereum blockchain access point.

      LOCAL_RPC_URL= <your_Ethereum_remote_RPC_endpoint>
      SOCKET_RPC_URL=<Your_Ethereum_remote_RPC_WebSocket_endpoint>
      ETH_PRIV_KEY=<Your_Ethereum_Private_Key_to_Address>
      
Example:

      LOCAL_RPC_URL=https://arb-rinkeby.g.alchemy.com/v2/xxxx
      SOCKET_RPC_URL=wss://arb-rinkeby.g.alchemy.com/v2/xxxx
      ETH_PRIV_KEY=4xxxx
      
NB: Your Ethereum private key must match with the account that you are using on the Plenny Dapp!

### Configuration of LND Node

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
      
NB: Your LND configurations must match with the Lightning Node that you have verified on the Plenny Dapp!

### Configuration for restarting the Application

The environment variable listed below are used to restart the DLSP application.
Restart option is provided, so the user can set the interval on how many seconds/minutes/hours the oracle application should be restarted - Just in case the application has stopped working due to some issue.

      ALLOW_AUTO_RESTART=true/false
      RESTART_INTERVAL_SECONDS=Your_restart_interval_seconds
      AVERAGE_DAILY_BLOCK_COUNT=Your_average_daily_block_count

Example:

      ALLOW_AUTO_RESTART=true
      RESTART_INTERVAL_SECONDS=3600
      AVERAGE_DAILY_BLOCK_COUNT=6500  

### Running Lightning Oracle 	

**Linux:**

Before running the Lightning Oracle binary, you must export the .env environment variables. You can use the script below.

      export $(grep -v '^#' .env | xargs)
      
After that you can execute the binary.

      root@9862fe3ba05c:~/PlennyOracle_Linux_x86_64# ls -la
            PlennyOracle build .env node_modules rpc.proto server
      root@9862fe3ba05c:~/PlennyOracle_Linux_x86_64# ./PlennyOracle
      
**Windows:**

Execute the PlennyOracle.exe file and this will up and run a Lightning Oracle service.

### Firewall Settings

To ensure high security, we ask that you open HTTPS 443 and Lightning Network Daemon (lnd) port 9735 to the public internet. For reference firewall settings, please see our Lightning Oracle simple architecture diagram.
