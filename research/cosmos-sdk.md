# cosmos sdk

## Transaction handling

The application part of the SDK handles tx's as follows:

1. Decode `transactions` received from Tendermint consensus engine
2. Extract `messages` from `transactions` and do basic sanity checks.
3. Route each message to the appropriate module so that it can be processed.
4. Commit state changes.

## baseapp

`baseapp` is the basic boilerplate for the app. comes with ABCI to connect to consensus. typically baseapp is extended by your app.

## multistore

`multistore` holds the state. holds multiple `KVStore` in order to divide state. KVStore only accepts `[]byte` type.

## modules

each module can be seen as a little state machine, and has its own `KVStore` in the multistore to persist the subset of state it defines. cosmos sdk is open source, so some modules may be malicious, so there you need security between modules. this is based on *object capabilities*. each module implements `keepers` that can be passed to other modules to grant capabilities.

## node client

daemon or full node client is the core process. is run as binary. binary is built by `main.go` in `./cmd/appd/`. the `start` command creates instance of state machine defined in `app.go`, init state machine with last known state found in `~/.app/data`, create and start new tendermint instance (which connects to peers, starts syncing, etc).

## core app

core of state machine is defined in `app.go`. this contains the type def for the app, and functions to initialize it. the type def contains:

* reference to `baseapp`. the app uses `baseapp`'s methods route tx to module. baseapp has core logic like ABCI methods, routing logic.
* list of store keys (keys for the key-value store)
* list of module's keepers. each module has keepers which handle read/write for that modules store(s). keeper's methods of one module can be called from other modules if authed.
* reference to an `appCodec` to serialize/deserialize data in order to store
* reference to `legacyAmino` codec. needed for now.
* reference to a module manager and a basic module manager. contains list of app's module for registering msg service etc.
