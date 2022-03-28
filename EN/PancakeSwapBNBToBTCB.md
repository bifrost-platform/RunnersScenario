```meta-Currency
btcb
```

# Swap BNB to BTCB in PancakeSwap

In this scenario, you will swap BNB to BTCB in PancakeSwap.

### Type in asset to swap.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient BNB.");
```

```output-Dynamic BTCB
let btcbAmount = Q.pancake.getAmountsOutFromExactIn("btcb", amountIn);
print(btcbAmount);
```

### Swap BNB to BTCB.

- Default PancakeSwap slippage (0.5%)

```taster
// Swap BNB to BTCB.
Q.pancake.swapExactBNBForTokens("btcb", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
