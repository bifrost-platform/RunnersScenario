```meta-Currency
link
```

# Swap ETH to LINK in SushiSwap

In this scenario, you will swap ETH to LINK.

### Set the amount of ETH to swap.

- The amount of LINK available with your ETH will be automatically calculated.
- Only the maximum amount of LINK available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient.

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient ETH.");
```

```output-Dynamic LINK
let linkAmount = Q.sushi.getAmountOut ("eth", "link", amountIn);
print(linkAmount);
```

### Swap ETH to LINK in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap ETH to LINK.
Q.sushi.sell ("eth", "link", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
