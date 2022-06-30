```meta-Currency
ousdt
```

# Swap KLAY to oUSDT in KLAYswap

In this scenario, you will swap KLAY to oUSDT.

### Set the amount of KLAY to swap.

- The amount of oUSDT available with your KLAY will be automatically calculated.
- Only the maximum amount of oUSDT available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic oUSDT
let ousdtAmount = Q.klay.getAmountOut("klay", "ousdt", amountIn);
print(ousdtAmount);
```

### Swap KLAY to oUSDT in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to oUSDT.
Q.klay.sell ("klay", "ousdt", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
