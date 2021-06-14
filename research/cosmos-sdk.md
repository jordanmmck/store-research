# cosmos sdk

## Transaction handling

The application part of the SDK handles tx's as follows:

1. Decode `transactions` received from Tendermint consensus engine
2. Extract `messages` from `transactions` and do basic sanity checks.
3. Route each message to the appropriate module so that it can be processed.
4. Commit state changes.

## baseapp

`baseapp` is the basic boilerplate for the app. comes with ABCI to connect to consensus. typically baseapp is extended by your app.
