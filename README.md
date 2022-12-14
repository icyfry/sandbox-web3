# Sandbox Web3

This repo is a basic **Ethereum** sandbox for local experiments

## References

* https://ethereum.org/en/developers/

* https://medium.com/compound-finance/setting-up-an-ethereum-development-environment-7c387664c5fe

* [Learn Blockchain, Solidity, and Full Stack Web3 Development with JavaScript – 32-Hour Course](https://www.youtube.com/watch?v=gyMwXuJrbJQ)

    * https://github.com/smartcontractkit/full-blockchain-solidity-course-js#setting-up-your-first-contract
    * https://github.com/PatrickAlphaC

## Init workspace

The sandbox workspace is designed to work with WSL on Windows

### EVM

Check connectivity to EVM from WSL
```
ping "$(hostname).local"
nc -zv "$(hostname).local" 7545
```

### WSL Setup

the configuration `localhostForwarding=true` need to be setup in [.wslconfig](https://docs.microsoft.com/en-us/windows/wsl/wsl-config#wslconfig) if Gnache is running by windows.

### Prerequisites tools

* npx `sudo npm install -g npx`
* nodejs 16.x [nodejs](https://nodejs.org/en/)
* vue.js [vitejs](https://vitejs.dev/)
* taskfile [taskfile.dev](https://taskfile.dev/installation/)
* Truffle & Ganache [trufflesuite](https://trufflesuite.com/)
    * `npm install -g truffle`
    * [vscode add-on](https://marketplace.visualstudio.com/items?itemName=trufflesuite-csi.truffle-vscode)

After installing the tools

```
task init
```

## Smart Contracts

Contracts are located in `./contracts` , to build the contracts with **solc** use the following command. Results will be located in `./build/contracts`

Tests and deploy are using **Hardhat**

Build and run tests on smart contracts

```
task contracts-build
task contracts-test
```

Deploy on local blockchain (using Ganache) . To launch ganache use `npx ganache-cli` or `ganache Windows app` [Ganache docs](https://trufflesuite.com/docs/ganache/)

```
task contracts-deploy-local
```

## DApp (Vue.js)

A sample [DApp](https://en.wikipedia.org/wiki/Decentralized_application) using Vue.js framework.

### DApp References

* https://blog.logrocket.com/integrate-web3-into-vue/


## Ethereum client

Use of (go-ethereum)[https://github.com/icyfry/go-ethereum]

* https://geth.ethereum.org/docs/install-and-build/installing-geth#docker-container

* https://medium.com/mercuryprotocol/dev-highlights-of-this-week-cb33e58c745f

```
docker pull ethereum/client-go
docker run -it -p 30303:30303 ethereum/client-go
docker stop ethereum/client-go
docker pull ethereum/client-go:latest
ethereum/client-go:alltools-latest 
```