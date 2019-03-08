# Key Terms

> This section provides definitions for various terms on the testnet trading page.

## "Balances" Component

On the [testnet trading page](testnet.qume.io/trade), you can see your current account balances in the "Balances" component.

| Field | Description | Formula
| --- | --- | --- |
| **Wallet Balance** | Total balance in your wallet | Deposits - Withdrawals + Realized P&L
| **Total Margin** | Total equity within the exchange | Wallet Balance + Unrealized P&L
| **Open Positions Margin** | Total margin posted for open positions  | (Avg. Entry Value / Leverage) + Unrealized P&L
| **Active Orders Margin** | Total margin posted for active orders | Avg. Value of Active Orders / Leverage
| **Available Margin** | Margin available for new positions | Total Margin - Open Positions Margin - Active Orders Margin

## "Open Positions" Section

The "Open Positions" section shows all of your positions that have not been closed or liquidated.

| Field | Description
| --- | --- |
| Size | Number of contracts
| Value | Notional value in BTC
| Entry Price | Price at which the position was opened
| Mark Price | See [Mark Price calculations](trading.md)
| Liq. Price | Estimated Mark Price that trigger liquidation
| Margin | Amount of margin reserved by the position
| Eff. Lvg. | Entry Value / (Initial Margin requirement + Unrealized P&L)
| Unrealized P&L | See [P&L calculations](trading.md)
| ROE% | Return on equity percentage
| Realized P&L | See [P&L calculations](trading.md)


## "Active Orders" Section

The "Active Orders" section shows all of your orders that have not yet been filled.

| Field | Description
| --- | --- |
| Type | Buy (long) or Sell (short)
| Time in Force | See [order types](ordertypes.md)
| Filled | # contracts filled out of the specified (limit) order size
| Remaining | # contracts unfilled out of the specified (limit) order size
| Limit Price | See [order types](ordertypes.md)
| Fill Price |  Average price of all fills in the order
| Value | Notional value in BTC
| Stop Price | See [order types](ordertypes.md)
| Time | Time at which the order was placed
