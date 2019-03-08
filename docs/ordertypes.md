# Order Types

## Market
A Market Order is an order to buy or sell at the best-available market price.

- Market orders are guaranteed to be executed
- Execution price is not guaranteed

## Limit
A Limit Order is an order to buy (sell) at a specific price or better.

- A limit buy can only be executed at the limit price or lower
- A limit sell can only be executed at the limit price or higher
- Limit orders are not guaranteed to execute.

## Stop Market
A Stop Order, or stop-loss order, is an order to buy (sell) after a specified stop price is reached. When the stop price is reached, a market order is placed automatically.

## Stop Limit
A Stop Limit Order will be executed at a specified limit price, or better, after a specified stop price has been reached. Once the specified stop price is reached, a limit order is immediately placed at the specified limit price.

On the Qume testnet, the specified stop price can be either the Mark Price or the Last Price.

## Time In Force Options

### “GoodTillCancel”

Your order will remain active until (1) the order is filled or (2) the order is cancelled.

### “ImmediateOrCancel”

Any unfilled portion of your order immediately after placement is cancelled.

### “FillOrKill”
Your order will only execute if the full quantity is filled immediately after placement.

### "Post Only"
A Post-Only Order will never match (against resting orders in the order book) immediately after placement. This ensures that the order is always on the maker side.
