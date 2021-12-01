```meta-Currency
btcb
```

# Swap BNB to BTCB in SushiSwap

In this scenario, you will swap BNB to BTCB.

### Set the amount of BNB to swap.

- The amount of BTCB available with your BNB will be automatically calculated.
- Only the maximum amount of BTCB available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient. (BNB will be consumed according to the available balance to swap.)

```input-Dynamic BNB
let amountIn = 1.0;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance (), "Insufficient BNB.");
```

```output-Dynamic BTCB
let btcbAmount = Q.sushi.getAmountsOutFromExactIn ("btcb", amountIn);
print (btcbAmount);
```

### Swap BNB to BTCB in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap BNB to BTCB.
Q.sushi.swapExactBNBForTokens ("btcb", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
