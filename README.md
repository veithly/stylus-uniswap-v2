# Stylus Uniswap V2

A Rust implementation of Uniswap V2-style AMM (Automated Market Maker) for the Arbitrum Stylus platform. Built using the [stylus-sdk](https://github.com/OffchainLabs/stylus-sdk-rs).

## Features

- ERC20 token implementation
- Automated Market Maker (AMM) functionality
- Liquidity provision and removal
- Token swaps
- Price oracle using cumulative prices
- Written in Rust for optimal performance
- Fully compatible with Ethereum ABI

## Quick Start

### Prerequisites

1. Install [Rust](https://www.rust-lang.org/tools/install)
2. Install Stylus CLI:
```bash
cargo install --force cargo-stylus cargo-stylus-check
```

3. Add WASM target:
```bash
rustup target add wasm32-unknown-unknown
```

### Installation

```bash
git clone https://github.com/veithly/stylus-uniswap-v2.git
cd stylus-uniswap-v2
```

### Build & Test

```bash
# Build contracts
cargo build

# Run tests
cargo test

# Export ABI
cargo stylus export-abi
```

## Deployment

1. Configure environment:
```bash
# Create .env file with:
RPC_URL=https://sepolia-rollup.arbitrum.io/rpc
PRIV_KEY_PATH=<path to private key file>
```

2. Check deployment:
```bash
cargo stylus check
```

3. Deploy contracts:
```bash
cargo stylus deploy --private-key-path=<PRIVKEY_FILE_PATH>
```

## Usage Examples

```rust
// Initialize pair
let pair = UniswapV2Pair::new(token0, token1);

// Add liquidity
pair.mint(to)?;

// Swap tokens
pair.swap(amount0Out, amount1Out, to)?;
```

See `examples/counter.rs` for more detailed examples.

## Architecture

The project consists of two main components:

- `erc20.rs`: Implementation of ERC20 token standard
- `lib.rs`: Core AMM logic including:
  - Liquidity pool management
  - Price calculations
  - Swap functionality
  - Oracle price accumulation

## Contributing

Contributions are welcome! Please check out our [contributing guidelines](.github/pull_request_template.md).

## Testing

Run the test suite:
```bash
cargo test
```

## Resources

- [Stylus Documentation](https://docs.arbitrum.io/stylus)
- [Testnet Information](https://docs.arbitrum.io/stylus/reference/testnet-information)

## License

This project is licensed under either:
- [Apache License, Version 2.0](licenses/Apache-2.0)
- [MIT License](licenses/MIT)

at your option.
