```meta-Currency
wbtc
```

# Swap ETH to WBTC in SushiSwap

In this scenario, you will swap ETH to WBTC.

### Set the amount of ETH to swap.

- The amount of WBTC available with your ETH will be automatically calculated.
- Only the maximum amount of WBTC available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient. (ETH will be consumed according to the available balance to swap.)

```input-Dynamic ETH
let amountIn = 1.0;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance (), "Insufficient ETH." );
```

```output-Dynamic WBTC
let wbtcAmount = Q.sushi.getAmountsOutFromExactIn ("wbtc", amountIn);
print (wbtcAmount);
```

### Swap ETH to WBTC in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap ETH to WBTC.
Q.sushi.swapExactETHForTokens ("wbtc", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
