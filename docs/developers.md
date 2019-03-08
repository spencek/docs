# Developer References

## API Connectivity

The Qume testnet offers low-latency REST and WebSocket APIs. Use these APIs to create custom trading systems and clients. See our [documentation](http://qume.docs.apiary.io) for implementation details.

The private REST API allows users to:

- see open positions
- place orders
- cancel orders
- see balances
- modify leverage and margin

The public REST API provides specific market data upon request, including:

- order book data
- trade history
- price indices


The public WebSocket API streams market data in real-time:

- order book snapshots
- trade events

## Matching Rules

The testnet operates a centralized limit order book matching engine. Matching is based on the “first come first serve” principle, or “FIFO”:

- Price and time are the only criteria for filling an order
- All orders at the same price level are filled according to time priority


## Risk Engine

The Qume Risk Engine continuously audits transactions and balances to ensure solvency at all times. These processes are executed asynchronously to ensure that latency remains as low as possible.


## Colocation

Testnet servers are located in Amazon’s `eu-west-1 region`. We do not offer specific co-location services.
