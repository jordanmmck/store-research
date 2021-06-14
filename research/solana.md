# solana

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
