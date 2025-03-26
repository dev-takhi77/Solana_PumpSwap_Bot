# PumpSwap SDK
# Solana Raydium Bundler & Pumpfun Bundler

This bot is designed to to buy and sell tokens in PumpSwap that migrated from pumpfun.

## Features

- **Presimulation**: Estimate token amount and Sol amount needed for bundler wallets.
- **Token Creation**: Create new token with vanity address.
- **Launch New Pool**: Create Market in raydium and create pool in Raydium. Create new pool in Pumpfun.
- **Bundle Buy**: Buying with more than 20 wallets in the same block.
- **Sell Mode**: Gradually sells all tokens in sub-wallets through small transactions or Sell at once from all sub-wallets.
- **Token CA Settings**: Configurable token mint with Vanity address.
- **Logging**: Supports adjustable logging levels for better monitoring and debugging.

## Usage
1. Clone the repository
```
git clone https://github.com/PioSol7/Solana_PumpSwap_Bot.git
cd Solana_PumpSwap_Bot
```
2. Install dependencies
```
npm install
```
3. Configure the environment variables

Rename the .env.example file to .env and set RPC and WSS, main keypair's secret key and all settings in settings.ts file.

4. Run the bot

```
npm start
```
### Buy token through cli
`
ts-node src/buy-cli.ts --token <ADDRESS_TOKEN> --sol <NUMBER_OF_SOL>
`

### Sell token through cli
`
ts-node src/sell-cli.ts --token <ADDRESS_TOKEN> --percentage <SELL_PERCENTAGE>
`

### buy/sell on PumpSwap
```typescript
import {wallet_1} from "./constants";
import {PumpSwapSDK} from './pumpswap';
async function main() {
    const mint = "your-pumpfun-token-address";
    const sol_amt = 0.99; // buy 1 SOL worth of token using WSOL
    const sell_percentage = 0.5; // sell 50% of the token
    const pumpswap_sdk = new PumpSwapSDK();
    await pumpswap_sdk.buy(new PublicKey(mint), wallet_1.publicKey, sol_amt); // 0.99 sol
    await pumpswap_sdk.sell_percentage(new PublicKey(mint), wallet_1.publicKey, sell_percentage);
    await pumpswap_sdk.sell_exactAmount(new PublicKey(mint), wallet_1.publicKey, 1000); // 1000 token
}
```

### Fetch the price
```typescript
import {getPrice} from './pool';
async function main() {
    const mint = new PublicKey("your-pumpfun-token-address");   
    console.log(await getPrice(mint));
}
```

### Fetch the pool
```typescript
import {getPumpSwapPool} from './pool';
async function main() {
    const mint = new PublicKey("your-pumpfun-token-address");   
    console.log(await getPumpSwapPool(mint));
}
```

    ## Author
    
    Discord: Takhi77 in discord
    
    Telegram: [@Takhi](https://t.me/@Takhi_77)
    
    You can always feel free to find me here for my help on other projects.


