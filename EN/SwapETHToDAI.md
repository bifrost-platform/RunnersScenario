```meta-Currency
dai
```

# Swap ETH to DAI in SushiSwap

In this scenario, you will swap ETH to DAI.

### Set the amount of ETH to swap.

- The amount of DAI available with your ETH will be automatically calculated.
- Only the maximum amount of DAI available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient. (ETH will be consumed according to the available balance to swap.)

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance (), "Insufficient ETH." );
```

```output-Dynamic DAI
let daiAmount = Q.sushi.getAmountsOutFromExactIn ("dai", amountIn);
print (daiAmount);
```

### Swap ETH to DAI in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap ETH to DAI.
Q.sushi.swapExactETHForTokens ("dai", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
