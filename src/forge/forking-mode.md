## Forking mode

Forge supports testing in a forked environment.

To run tests in a forked environment - such as a forked Ethereum mainnet - pass a RPC URL via the `--fork-url` flag:

```bash
forge test --fork-url <your_rpc_url>
```

The following values are changed to reflect those of the chain at the moment of forking:

- [`block_number`](../reference/config.md#block_number)
- [`chain_id`](../reference/config.md#chain_id)
- [`gas_limit`](../reference/config.md#gas_limit)
- [`gas_price`](../reference/config.md#gas_price)
- [`block_base_fee_per_gas`](../reference/config.md#block_base_fee_per_gas)
- [`block_coinbase`](../reference/config.md#block_coinbase)
- [`block_timestamp`](../reference/config.md#block_timestamp)
- [`block_difficulty`](../reference/config.md#block_difficulty)

It is possible to specify a block from which to fork with `--fork-block-number`:

```bash
forge test --fork-url <your_rpc_url> --fork-block-number 1
```

Forking is especially useful when you need to interact with existing contracts, and you may choose to do integration testing this way, as if you were on an actual network.

### Caching

If both `--fork-url` and `--fork-block-number` are specified, then data for that block is cached for future test runs.

The data is cached in `~/.foundry/cache/<chain id>/<block number>`. To clear the cache, simply remove the directory.

It is also possible to ignore the cache entirely by passing `--no-storage-caching`, or with `foundry.toml` by configuring [`no_storage_caching`](../reference/config.md#no_storage_caching) and [`rpc_storage_caching`](../reference/config.md#rpc_storage_caching).

### Improved traces

Forge supports identifying contracts in a forked environment with Etherscan.

To use this feature, pass the Etherscan API key via the `--etherscan-api-key` flag:

```bash
forge test --fork-url <your_rpc_url> --etherscan-api-key <your_etherscan_api_key>
```

Alternatively, you can set the `ETHERSCAN_API_KEY` environment variable.
