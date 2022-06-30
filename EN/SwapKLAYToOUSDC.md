```meta-Currency
ousdc
```

# Swap KLAY to oUSDC in KLAYswap

In this scenario, you will swap KLAY to oUSDC.

### Set the amount of KLAY to swap.

- The amount of oUSDC available with your KLAY will be automatically calculated.
- Only the maximum amount of oUSDC available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic oUSDC
let ousdcAmount = Q.klay.getAmountOut("klay", "ousdc", amountIn);
print(ousdcAmount);
```

### Swap KLAY to oUSDC in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to oUSDC.
Q.klay.sell ("klay", "ousdc", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
