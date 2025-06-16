# MCP Swap Server

An MCP (Model Context Protocol) example server for Chrom.ar, using the @chrom-ar/mcp-base package.

## Installation

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```
3. Build the project:
   ```bash
   npm run build
   ```

## Usage

### Development
```bash
npm run dev
```

### Production
```bash
npm start
```

## MCP Tools

### 1. `get-swap-quote`
Get a price quote for a token swap without building transactions.

**Parameters:**
- `amount`: Amount to swap (as string)
- `fromToken`: Source token symbol (e.g., "USDC", "ETH")
- `toToken`: Target token symbol
- `fromAddress`: User's wallet address
- `fromChain`: Blockchain name ("ETHEREUM", "ARBITRUM", etc.)
- `mode` (optional): Trading mode - "market" (default)
- `slippage` (optional): Slippage tolerance as percentage (default: 0.5)

**Example:**
```json
{
  "amount": "100",
  "fromToken": "USDC",
  "toToken": "USDT",
  "fromAddress": "0x742d...",
  "fromChain": "ETHEREUM",
  "mode": "market",
  "slippage": 0.5
}
```

### 2. `build-swap-transactions`
Build unsigned transactions ready for signing.

**Parameters:** Same as `get-swap-quote`

**Returns:**
- Array of unsigned transactions (approval + swap)
- Quote information
- Trading mode used

## Trading Mode

### Market Mode
- Traditional DEX aggregation
- Immediate execution
- User submits transactions directly
- Best for trades requiring immediate settlement

## Supported Chains

- **Ethereum** (chainId: 1)
- **Arbitrum One** (chainId: 42161)
- **Optimism** (chainId: 10)
- **Base** (chainId: 8453)
- **Polygon** (chainId: 137)
- **Avalanche** (chainId: 43114)

## Supported Tokens

### Ethereum
- USDC: `0xA0b86a33E6441031aAd3f2bEDf49EC5Bc2f42E45`
- USDT: `0xdAC17F958D2ee523a2206206994597C13D831ec7`
- DAI: `0x6B175474E89094C44Da98b954EedeAC495271d0F`

### Arbitrum
- USDC: `0xFF970A61A04b1cA14834A43f5dE4533eBDDB5CC8`
- USDT: `0xFd086bC7CD5C481DCC9C85ebE478A1C0b69FCbb9`
- DAI: `0xDA10009cBd5D07dd0CeCc66161FC93D7c9000da1`

*(Additional chains and tokens supported - see `src/types/index.ts` for full list)*

## Environment Variables

Create a `.env` file:
```
NODE_ENV=production
SERVER_URL=https://my.public.domain/mcp
```

## Development

### Testing
```bash
npm test
```

### Building
```bash
npm run build
```

## License

MIT
