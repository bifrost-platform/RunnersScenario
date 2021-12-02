```meta-Currency
bfc
```

# Swap ETH to BFC in SushiSwap

In this scenario, you will swap ETH to BFC.

![title](https://raw.githubusercontent.com/bifrost-platform/RunnersScenario/master/imgs/ETHtoBFC.jpg)

### Set the amount of ETH to swap.

- The amount of BFC available with your ETH will be automatically calculated.
- Only the maximum amount of BFC available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient. (ETH will be consumed according to the available balance to swap.)

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient ETH.");
```

```output-Dynamic BFC
let bfcAmount = Q.sushi.getAmountsOutFromExactIn("bfc", amountIn);
print(bfcAmount);
```

### Swap ETH to BFC in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap ETH to BFC.
Q.sushi.swapExactETHForTokens("bfc", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
