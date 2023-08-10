# <div align="center">🎈 BridgeLottery 🎈</div>

```
888888b.           d8b      888                   888              888    888                             
888  "88b          Y8P      888                   888              888    888                             
888  .88P                   888                   888              888    888                             
8888888K.  888d888 888  .d88888  .d88b.   .d88b.  888      .d88b.  888888 888888 .d88b.  888d888 888  888 
888  "Y88b 888P"   888 d88" 888 d88P"88b d8P  Y8b 888     d88""88b 888    888   d8P  Y8b 888P"   888  888 
888    888 888     888 888  888 888  888 88888888 888     888  888 888    888   88888888 888     888  888 
888   d88P 888     888 Y88b 888 Y88b 888 Y8b.     888     Y88..88P Y88b.  Y88b. Y8b.     888     Y88b 888 
8888888P"  888     888  "Y88888  "Y88888  "Y8888  88888888 "Y88P"   "Y888  "Y888 "Y8888  888      "Y88888 
                                     888                                                              888 
                                Y8b d88P                                                         Y8b d88P 
                                 "Y88P"                                                           "Y88P"  
```
## 📚 What is BridgeLottery?

**BridgeLottery** is an open-source project that allows bridge owners to implement a lottery in just a few minutes.

### How it work?

Firstly, the **Bridgelottery** [script](https://github.com/BridgeLottery/script) listens for transactions on the bridge defined in the config.json file as the ```eventAddress``` for the time defined in the ```subscriptionDurationInSeconds``` variable. A smart contract called [depositor.sol](https://github.com/BridgeLottery/contracts) is deployed in parallel and each address of users who have used the bridge are mapped inside.

When ```subscriptionDurationInSeconds``` is over, the script then call the smart contract called [randomNumber.sol](https://github.com/BridgeLottery/contracts) using **[Chainlink](https://chain.link/)** to obtain a random number and selects the winner using this formula: ```randomNumberGeneratedFromChainlink % numberOfParticipants```. => The winner is then the address in the array corresponding to the result.

Finally, in the following example, the winner receives an attestation from **[EAS](https://attest.sh/)** certifying that he has won the lottery, with a timestamp indicating the date of the win. As the prize for the lottery, the winner also receives an NFT on **[Zora](https://zora.co/)** Goerli chain.

### Some examples :

- 🔴 [OP BridgeLottery Exemple](https://github.com/BridgeLottery/OPbridge_exemple)
- 🔵 [Base BridgeLottery Exemple](https://github.com/BridgeLottery/BASEbridge_exemple)
- 🟢 [Mode BridgeLottery Exemple](https://github.com/BridgeLottery/MODEbridge_exemple)

## 🖥️ Installation Guide

### 1/ Clone the smart contracts repository :

```git clone https://github.com/BridgeLottery/contracts```

### 2/ Deploy the smart contracts :

- Deploy [depositor.sol](https://github.com/BridgeLottery/contracts) using [Remix](https://remix.ethereum.org/)
- Deploy [randomNumber.sol](https://github.com/BridgeLottery/contracts) using [Remix](https://remix.ethereum.org/)

### 3/ Clone the script repository :

```git clone https://github.com/BridgeLottery/script```

### 4/ Install all the dependencies :

- Using npm : ```npm i```
- Using yarn : ```yarn```

### 5/ Set your keys into config.json :

- ```web3Key``` => The key of your RPC using websocket below
- ```web3Socket``` => Your RPC using websocket
- ```depositorContractAddress``` => The contract address of [depositor.sol](https://github.com/BridgeLottery/contracts) that you have deployed
- ```randomNumberContractAddress``` => The contract address of [randomNumber.sol](https://github.com/BridgeLottery/contracts) that you have deployed
- ```fromAddress``` => Your account address that you will use to send tx from the script
- ```privateKey``` => The private key of our account address that you will use to send tx from the script
- ```yourEndpointUrl``` => Your RPC using https
- ```yourEndpointKey``` => The key of your RPC using https above
- ```easContractAddress``` => The **[EAS](https://attest.sh/)** contract address
- ```gasEstimationKey``` => The key of your gas estimation service below
- ```gasEstimationUrl``` => Your gas estimation service using https
- ```schemaUID``` => The schema UID of your **[EAS](https://attest.sh/)** attestations

### 6/ Run the script :

```node script.js```

### 7/ Enjoy! 🎈🎈🎈

***<div align="center">Built w/ ❤️ @SuperHack2023</div>***
