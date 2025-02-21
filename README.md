# GOT & DeFi Protocol Solidity Contracts

## Overview
This repository contains two Solidity smart contracts deployed on the Binance Smart Chain (BSC):

1. **GOT Token Contract** - An ERC-20 token contract with the symbol **GOT**.
2. **Treasury Protocol Contract** - A smart contract managing Golden Pact DeFi fund allocations and protocol functionalities.

## Features

### GOT Token Contract
- Implements the ERC-20 standard.
- Supports standard token transfers, approvals, and balance queries.
- May include additional features such as minting, burning, or fee mechanisms (modify accordingly).

### Treasury Protocol Contract
- Manages Golden Pact fund allocations and DeFi-related functions.
- Handles interactions between GOT token holders and the protocol.
- May include liquidity management, staking, or other investment mechanisms (adjust details accordingly).

## Deployment

### Prerequisites
- [Node.js](https://nodejs.org/) and [pnpm](https://pnpm.io/) installed.
- [Hardhat](https://hardhat.org/) setup for Solidity development.
- A BSC-compatible wallet (e.g., MetaMask) configured.

### Installation
```sh
pnpm install
```

### Compile Contracts
```sh
npx hardhat compile
```

### Deploy to BSC Testnet/Mainnet
1. Configure the network in `hardhat.config.js`.
2. Deploy using:
```sh
npx hardhat run scripts/deploy.js --network bscTestnet
```

## Interactions

### Using Hardhat Console
Example of calling functions via Hardhat console:
```sh
npx hardhat console --network bscTestnet
```
```js
const GOT = await ethers.getContractAt("GOT", "<GOT_CONTRACT_ADDRESS>");
await GOT.transfer("0xRecipientAddress", ethers.utils.parseUnits("100", 18));
```

### Using Web3 or viem
Example interaction with viem:
```js
import { createPublicClient, http } from 'viem';
import { bsc } from 'viem/chains';

const client = createPublicClient({
  chain: bsc,
  transport: http()
});

const balance = await client.readContract({
  address: '<GOT_CONTRACT_ADDRESS>',
  abi: GOT_ABI,
  functionName: 'balanceOf',
  args: ['0xYourAddress']
});
```

## Testing
Run tests with:
```sh
npx hardhat test
```

## Security Considerations
- Always review contract security before deployment.
- Use tools like Slither and Hardhat security plugins to analyze vulnerabilities.
- Consider external audits before mainnet deployment.

## License
This repository is licensed under the MIT License. See [LICENSE](LICENSE) for details.

