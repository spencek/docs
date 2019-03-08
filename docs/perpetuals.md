# Perpetual Swap contracts

> Version 1.0 of the testnet supports a lone **Bitcoin / US Dollar Perpetual Inverse Swap Contract** market. Futures contracts will be added soon.

## Basics

A Bitcoin / USD Perpetual Swap Contract is an *inverse futures contract* with the following distinctions:

- No expiry, settlement, or delivery
- Periodic funding payments between longs and shorts keep the perpetual contract price tethered to the underlying spot asset price (unlike futures which may have a wide basis)

All traders using leverage should be familiar with the following:

- *Initial Margin* and *Maintenance Margin* determine the leverage with which a user can trade, and the price at which automatic liquidation is triggered. Maximum leverage for perpetual contracts is 100x.
- *Forced liquidation* is triggered when a user cannot fulfill their maintenance requirement. All maintenance margin is lost when liquidation occurs.
- The *Mark Price*, or fair price of the perpetual contract, is used to determine *unrealized P&L* and liquidation price.
- The *Qume Index* tracks the spot price of Bitcoin. It is average price across several spot exchanges.
- The *Funding Rate* is paid (received) daily at 08:00 UTC. You only pay (receive) funding if you hold a position at that exact time.
- Contracts are quoted in USD, but all profit/loss is realized in BTC (hence "inverse")

## Contract Specification

| Field | Value
| --- | --- |
| Symbol | BTCUSDQ |
| Type | Inverse (Quoted USD, Settled BTC)
| Expiry | None
| Underlying | Qume Index
| Contract Value | 1 USD
| Lot Size | 1
| Tick Size | 0.5 USD
| Funding | Every 24 Hours at 08:00 UTC
| Initial Margin | 1.00%
| Maintenance Margin | 0.5%
| Fair Price Index | Mark Price
| Forced Liquidation | Yes
| Max Price | 1,000,000
| Max Order Quantity | 10,000,000

## Qume (BTC) Index

The underlying asset for the BTC/USD Perpetual contract is the *Qume Index*, which tracks the spot price of Bitcoin.

- Every 10 seconds, the price is calculated by taking a simple average of spot BTC prices on multiple exchanges
- The index is composite; if one exchange goes down, that constituent is automatically removed from index calculations until service resumes

Simplified formula:

- Qume Index = $⅓$Bitstamp + $⅓$Gemini + $⅓$Coinbase Pro


## Funding Rate

The *Funding Rate* is presented as a daily interest rate. Funding is paid/received daily at 08:00 UTC. A user’s funding payment is equal to:

- Funding Payment = Funding Rate $\times$ Position Value

If the perpetual contract is trading higher than the spot price (Qume Index), longs make funding payments to the shorts. This makes the perpetual contract less attractive to longs and more attractive to shorts, pushing the price back down to the Qume Index price. If the perpetual contract trades lower than the index, the shorts pay longs, creating the inverse effect.

To calculate the Funding Rate at a given moment, first calculate the Premium Rate:

- Premium Rate = $\frac {[\text{Mark Price}-\text{Qume Index}]} {\text{Qume Index}}$

If Premium Rate is between -0.05% and 0.05%, inclusive, then the Funding Rate is reduced to zero.

If Premium Rate is lower than -0.05%, then the Funding Rate is equal to PremiumRate + 0.05%.

If the Premium rate is higher than 0.05%, then the Funding Rate is equal to the PremiumRate - 0.05%

Based on the Premium Rate, we calculate the current Funding Rate:

- **Funding Rate = max(0.05%, Premium Rate) + min(−0.05%, Premium Rate)**
