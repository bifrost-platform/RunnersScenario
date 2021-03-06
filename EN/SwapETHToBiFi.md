```meta-Currency
bifi
```

# Swap ETH to BiFi in SushiSwap

In this scenario, you will swap ETH to BiFi.

![title](/imgs/ETHtoBIFI.jpg)

### Set the amount of ETH to swap.

- The amount of BiFi available with your ETH will be automatically calculated.
- Only the maximum amount of BiFi available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient.

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient ETH.");
```

```output-Dynamic BIFI
let bifiAmount = Q.sushi.getAmountOut ("eth", "bifi", amountIn);
print(bifiAmount);
```

### Swap ETH to BiFi in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap ETH to BiFi.
Q.sushi.sell ("eth", "bifi", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
