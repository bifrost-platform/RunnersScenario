```meta-Currency
oeth
```

# Swap KLAY to oETH in KLAYswap

In this scenario, you will swap KLAY to oETH.

### Set the amount of KLAY to swap.

- The amount of oETH available with your KLAY will be automatically calculated.
- Only the maximum amount of oETH available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic oETH
let oethAmount = Q.klay.getAmountOut("klay", "oeth", amountIn);
print(oethAmount);
```

### Swap KLAY to oETH in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to oETH.
Q.klay.sell ("klay", "oeth", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
