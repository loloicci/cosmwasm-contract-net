# An Example of Non-deterministic Contract (using rand)

## Summary

In the `master` branch, both init and execute are non-deterministic.
~This wasm cannot store the chain.~
~To store the contract in the chain, specified non auto gas limit. For example, with "--gas='1000000'".~
This wasm cannot store the chain.
This is because https://github.com/CosmWasm/cosmwasm/blob/master/packages/vm/src/middleware/deterministic.rs judges float operator are non-deterministic.

## Compile and Execute
This section is summary of https://docs.cosmwasm.com/getting-started/compile-contract.html .
For set up the environment, see https://docs.cosmwasm.com/getting-started/installation.html and https://docs.cosmwasm.com/getting-started/setting-env.html .

To compile this to wasm suitable to use in CosmWasm, execute the follows.

```sh
docker run --rm -v "$(pwd)":/code \
  --mount type=volume,source="$(basename "$(pwd)")_cache",target=/code/target \
  --mount type=volume,source=registry_cache,target=/usr/local/cargo/registry \
  cosmwasm/rust-optimizer:0.9.0
```

Then, `contract.wasm` is the output.

To know how to install and execute the wasm, see https://docs.cosmwasm.com/getting-started/interact-with-contract.html .
It is a very kind documentation.
(However there is a bug. see also https://github.com/CosmWasm/docs2/issues/26 )
