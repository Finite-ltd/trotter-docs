## Introduction

All the configuration you need to do are stored in the `config.ts` directory and the `docker-compose.yml` file. Each option is self explanatory, so feel free to look through the files and get familiar with the options available to you.

Purpose of this document is to give you a good, high-level overview of how Trotter works. We believe by getting to know more of how Trotter works you will be more confident building your Trotter instance. 

To start with a list of EVM tested and recommended networks can be found on the `networks` in the `config.ts` file, they are listed below.

- Ethereum
- Binance Smart Chain
- Matic (polygon)

First deploy Trotter found in the `trotter/smart-contracts/contract/TrotterNftErc721.sol`
Next thing is to take the contract address and place it on your environment or if you use docker on the docker-compose.yml file within the environment variables using the following pattern:
`NFT_CONTRACT_{NETWORK}` eg for ethereum `NFT_CONTRACT_ETH_MAINNET`, below is list of supported networks and the variable names to store their contract addresses.

- `NFT_CONTRACT_MATIC_MAINNET`   
- `NFT_CONTRACT_ETH_MAINNET`    
- `NFT_CONTRACT_BSC_MAINNET`

After that you must add the network to `listedNetworks` on the `config.ts` file so the middleware picks it up when validating network on requests. Make sure you put the value to the listed network as erc721 if you deployed the `TrotterNftErc721.sol` smart contract and erc1155 if you deployed the `TrotterNft.sol` smart contract like so    
```listedNetworks: { 'MATIC_MAINNET': 'erc721', ... } ```

If you have followed these steps above you are good to go, just launch your Trotter instance and start calling the apis. More details of the structures and how to use apis in the next sections.