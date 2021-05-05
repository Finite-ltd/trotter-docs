# Introduction

When working with a tool the more understanding you have with how it works, the more comfortable you are using it. This doc is designed to 
carry you through the process requests go through and how Trotter responeds to requests from A-Z.

## LifeCycle Overview

### Authentication (Middlewares)
To keep the apis secured and so the developers are able to monitor and trace source of any glitch if at all it happens Trotter have been implemented with an auth middleware found in `middleware/auth.middleware.ts`. This means before you are able to call any Trotter api you must have been given access to the Trotter api by the admins. So for every request Trotter validates the user with `Basic auth` which means you need to send your `username` and `password` in `authorization` header.

### Networks (Middlewares)

As explained in the installation Trotter works on multiple EVM based blockchains so it needs to validate and know which network a client is trying to communicate on each requests. 
Trotter handles this with a network middleware found in `middleware/networks.middleware.ts`.   
   
When a request reaches the Trotter api the network middleware looks for a `network` header found in `req.headers.network` as expressed in the middleware file on line 6. To ensure that the network has been deployed and Trotter have the contract address and it has been listed as a supported networks Trotter then takes this network name and look it up on the `config.contracts` and `config.listedNetworks` in the config file once it is able to verify that the contract address is available and we have it listed on our supported network list Trotter allows the request to go through. By default you can set a default network on the environment eg `API_DEFAULT_NETWORK=API_ETH_TESTNET` or whatever network you want as default, if a request does not have network specified on the headers, Trotter takes the default network and proceeds.



#### Controllers

When a request passes all required middleware then it goes to the controller, on our controller we simply take data from parameters, query and headers and send them to our services to get proccessed when this is complete a response is being sent from service to controller back to client with appropriate message and status codes.
