# Intro Polygon zkEVM

This project is a simple fullstack dApp that allows users to mint a blockchain name as an NFT on Polygon zkEVM.

## Getting started

1. Clone the repo

```sh
git clone https://github.com/nunocgoncalves/intro-polygon-zkevm.git
```

2. Install dependencies

```sh
yarn
```

3. Copy the .env.example file and add your private key

```sh
cp .env.example .env
```

4. Get some Goerli test ETH ([faucet](https://goerlifaucet.com/))

5. Bridge to the zkEVM testnet using the [zkEVM Bridge](https://public.zkevm-test.net/)

6. Setup Hardhat

- Add zkEVM to the ``hardhat.config.js``

```js
networks: {
    zkEVM: {
      url: `https://rpc.public.zkevm-test.net`,
    },
},
```

### Deploy the contract

``sh
npx hardhat run scripts/deploy.js --network zkEVM
``

### Connect the contract to the frontend

1. Get the contract ABI

- Copy the contract ABI from ``artifacts/contracts/Domains.sol/Domains.json`` to ``app/src/utils/``
- Rename it to contractABI.json

2. Add the zkEVM network to the frontend

- Add it to the network utils ``app/src/utils/networks.js``

```js
const networks = {
    ...
    "0x5122": "Polygon zkEVM",
}
```

- Tweak ``useEffect`` and ``switchNetwork`` in ``app/src/App.js``

3. Add contract address in ``app/src/App.js``

## Resources

- [How to build your own DNS by buildspace](https://buildspace.so/p/build-polygon-ens)
