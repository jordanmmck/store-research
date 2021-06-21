# solana

## high level

* contracts are written in Rust
* contracts import Solana Rust library with blockchain/solana specific commands. hash functions etc.
* 950 nodes
* 400 ms blocktimes
* no mempool?
* sub second finality
* no sharding or L2s

## proof of history

* the problem is deciding on time in a distributed adversarial system.
* you can prove a message happened after an event by putting details of the event into your message.
* uses verifiable delay function: basically does a hash chain and periodically records the count and the current output. so then you know time has passed between each count and that the ordering of your checkpoints is legit.
* you record messages into the chain, which impacts the hash at that point forward. then looking at the chain you can be sure that the given data existed at a given point
* so you can check all the slices in parallel. though you have to generate them in serial.
* possibly churn out hash chain pretty much maxing out node resources. can’t really brute force this. can’t parallelize it. that sets the time roughly. X links in this chain per second for modern CPU.

## hello world

[repo](https://github.com/solana-labs/example-helloworld/blob/master/README.md)

```zsh
solana config set --url localhost
solana-keygen new
solana-test-validator
npm run build:program-rust
```

The build command runs this:

```zsh
cargo build-bpf --manifest-path=./src/program-rust/Cargo.toml --bpf-out-dir=dist/program
```

So we are simply compiling the rust program to the BPF format using `build-bpf`. Next we deploy:

```zsh
solana program deploy dist/program/helloworld.so
```

This creates 200+ tx's on the local Solana chain. We can then invoke the on-chain program from the `hello_world.ts` typescript code. The functions called are from the `@solana/web3.js` package.
