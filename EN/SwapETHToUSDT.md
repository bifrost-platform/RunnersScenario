```meta-Currency
usdt
```

# Swap ETH to USDT in SushiSwap

In this scenario, you will swap ETH to USDT.

### Set the amount of ETH to swap.

- The amount of USDT available with your ETH will be automatically calculated.
- Only the maximum amount of USDT available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient.

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient ETH.");
```

```output-Dynamic USDT
let usdtAmount = Q.sushi.getAmountsOutFromExactIn("usdt", amountIn);
print(usdtAmount);
```

### Swap ETH to USDT in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap ETH to USDT.
Q.sushi.swapExactETHForTokens("usdt", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
