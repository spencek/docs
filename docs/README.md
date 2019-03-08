# Qume Testnet

> A simulated exchange platform that offers full trading functionality using test funds

> Qume was built with an emphasis on API performance. Our core backend system is stable, but we are still working on fixing bugs and improving performance in our front-end application. If you run into any problems on our website, please contact us.

## Introduction

The testnet is a production environment where traders can validate exchange functionality without transacting real funds.

- Use the [web application](testnet.qume.io) to place orders and manage account settings
- Use our REST and WebSocket APIs ([link to docs](qume.docs.apiary.io)) to implement custom trading systems

We currently support a **Bitcoin / US Dollar Perpetual Inverse Swap Contract** market with up to **100x leverage**.

## Performance

Our core trading engine is optimized to provide extremely low-latency response-times for API requests. The Qume matching engine can support 100,000 transactions per second in each market. Across all markets, our system is capable of processing millions of transactions per second.

- Mean latency for an order to be matched by our trading engine is 300 microseconds
- Mean round-trip latency (from external API request to response) is 2 milliseconds for REST calls and 800 microseconds for FIX operations (FIX is not included in testnet version 1.0)
- 99.9% of requests are returned in <10 milliseconds

## Test Funds

**Test Bitcoin is used for all transactions on the testnet. These coins have no monetary value.**

- Your account is automatically credited with 1 BTC
- No deposits or withdrawals
- Email [admin@qume.io](admin@qume.io) to request additional funds



## Market Simulator

The testnet runs an automated market-simulator that places trades on the exchange to simulate real-time market activity.

## Fees

**The testnet does not take any transaction fees.** Calculations for Margin, P&L and other relevant figures may differ significantly from margin trading platforms that do take fees.
