```meta-Currency
usdt
```

# Swap BNB to USDT in SushiSwap

In this scenario, you will swap BNB to USDT.

### Set the amount of BNB to swap.

- The amount of USDT available with your BNB will be automatically calculated.
- Only the maximum amount of USDT available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient BNB.");
```

```output-Dynamic USDT
let usdtAmount = Q.sushi.getAmountsOutFromExactIn("usdt", amountIn);
print(usdtAmount);
```

### Swap BNB to USDT in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap BNB to USDT.
Q.sushi.swapExactBNBForTokens("usdt", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
