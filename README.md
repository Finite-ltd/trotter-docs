## Trotter

> High-level API library for creating NFT tokens

Trotter does abstraction on creation of NFT tokens on multiple EVM-based blockchain networks.

We provide a simple interface that's highly configurable.


### Installation
## Prepare & run

> mkdir -p mongodb/database

> docker-compose up -d

## Testing it out

Find what is local IP of the trotter docker container:

> docker inspect trotter | grep "IPAddress"

Open your favorite browser and open this IP:

> $DOCKER_IP_ADDRESS:3000/api

Play!

## Configuration

Configuration is done via environment variables.

### database
> MONGODB_URL=

### RPC endpoints
> API_MATIC_TESTNET="https://rpc-mumbai.maticvigil.com/"

> API_MATIC_MAINNET="https://rpc-mainnet.maticvigil.com/"

> API_ETH_TESTNET="https://rinkeby.infura.io/v3/{infura-key}"

> API_ETH_MAINNET="https://mainnet.infura.io/v3/{infura-key}"

> API_BSC_TESTNET="https://data-seed-prebsc-1-s1.binance.org:8545"

> API_BSC_MAINNET="https://bsc-dataseed.binance.org"

### private key seed (for admin account)
> WALLET=

### prod | develop
TROTTER_NODE_ENV=develop 

