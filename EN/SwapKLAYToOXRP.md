```meta-Currency
oxrp
```

# Swap KLAY to oXRP in KLAYswap

In this scenario, you will swap KLAY to oXRP.

### Set the amount of KLAY to swap.

- The amount of oXRP available with your KLAY will be automatically calculated.
- Only the maximum amount of oXRP available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic oXRP
let kxrpAmount = Q.klay.getAmountOut("klay", "oxrp", amountIn);
print(kxrpAmount);
```

### Swap KLAY to oXRP in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to oXRP.
Q.klay.sell ("klay", "oxrp", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
