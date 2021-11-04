# chainlink

## v1

- reputation contract
  - tracks reputation of oracle-service-providers
- order-matching contract
  - takes proposed SLA, logs parameters, and collects bids from oracle providers
  - selects bids using rep contract
- aggregating contract
  - asdf

> Blockchain oracles are often viewed today as decentralized services with one objective: to forward data from off-chain resources onto blockchains. It’s a short step, though, from forwarding data to computing on it, storing it, or transmitting it bidirectionally

>  In short, an oracle can and will need to be a general-purpose, bidirectional, compute-enabled interface between and among onchain and off-chain systems

commit-reveal: commit hashes of some data. then reveal in next round.

threshold signatures:
