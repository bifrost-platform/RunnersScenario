```meta-Currency
owbtc
```

# Swap KLAY to oWBTC in KLAYswap

In this scenario, you will swap KLAY to oWBTC.

### Set the amount of KLAY to swap.

- The amount of oWBTC available with your KLAY will be automatically calculated.
- Only the maximum amount of oWBTC available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.
- As there is currently no pool for KLAY/oWBTC pair, you will exchange through one of KSP, oETH, or oUSDT tokens.
- ChainRunner Q will automatically choose the swap method for the highest amount of oWBTC in return.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic oWBTC
let owbtcAmount = Q.klay.getAmountOut("klay", "owbtc", amountIn);
print(owbtcAmount);
```

### Swap KLAY to oWBTC in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to oWBTC.
Q.klay.sell ("klay", "owbtc", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
