```meta-Currency
usdc
```

# Swap BNB to USDC in SushiSwap

In this scenario, you will swap BNB to USDC.

### Set the amount of BNB to swap.

- The amount of USDC available with your BNB will be automatically calculated.
- Only the maximum amount of USDC available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient. (BNB will be consumed according to the available balance to swap.)

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance (), "Insufficient BNB." );
```

```output-Dynamic USDC
let usdcAmount = Q.sushi.getAmountsOutFromExactIn ("usdc", amountIn);
print (usdcAmount);
```

### Swap BNB to USDC in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap BNB to USDC.
Q.sushi.swapExactBNBForTokens ("usdc", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
