# Oracles

The only information that blockchains know about is their internal state, block numbers, pow difficulty, etc. They cannot "see" the outside world. They do not themselves have any way of knowing the price of AMZN stock for example. Systems like Ethereum do not make API requests to http endpoints. The EVM is sand-boxed, it only knows about Ethereum state. All extrinsic data must be _brought_ on-chain.

For most blockchains, like ethereum for example, it is also the case that all transactions and code execution must be initiated by an outside source, ie. a person initiating the tx, or a computer somewhere which holds private keys which creates and signs tx's.

So the entire system is self-contained, in that it only knows its internal state, all other data must be sent in, and it is passive in that every process must be initiated by outside source — contract code cannot execute on its own.

There is of course motivation to have outside data brought on-chain. this is the domain of oracles.

## Truth vs. Ground Truth

There is some distinction, or at least gradation, to acknowledge in the oracle space of truth vs. ground truth.

For example, suppose we ask "what is the temperature in Las Vegas?". The oracle system might give us the reading of a single temperature sensor, or it maybe it will take the average of many sensors. Neither the reading of a single sensor, nor the average of many sensors can be said to be the _True_ temperature. Temperature will of course vary depending where its measured, accuracy of sensors, etc.

But if the oracle can bring those values on-chain as they are, in a tamper-resistant manner, then the oracle will have done its job.

So there is a distinction between bringing data on-chain in a fidelity preserving manner, and deciding what is true. ie. if we decide that a specific sensor will be the single source for Las Vegas temperature, then the oracle will have performed perfectly if it simply brings that read-out on-chain reliably. In this case it is not the job of the oracle to question whether that sensor is representative of the region, nor whether it is even functioning properly. The oracle simply brings that data, whatever it is, on-chain.
