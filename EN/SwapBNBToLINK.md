```meta-Currency
link
```

# Swap BNB to LINK in SushiSwap

In this scenario, you will swap BNB to LINK.

### Set the amount of BNB to swap.

- The amount of LINK available with your BNB will be automatically calculated.
- Only the maximum amount of LINK available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient BNB.");
```

```output-Dynamic LINK
let linkAmount = Q.sushi.getAmountOut ("bnb", "link", amountIn);
print(linkAmount);
```

### Swap BNB to LINK in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap BNB to LINK.
Q.sushi.sell ("bnb", "link", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
