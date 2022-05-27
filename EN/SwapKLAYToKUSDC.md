```meta-Currency
kusdc
```

# Swap KLAY to KUSDC in KLAYswap

In this scenario, you will swap KLAY to KUSDC.

### Set the amount of KLAY to swap.

- The amount of KUSDC available with your KLAY will be automatically calculated.
- Only the maximum amount of KUSDC available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic KUSDC
let kusdcAmount = Q.klay.getAmountsOutFromExactIn("kusdc", amountIn);
print(kusdcAmount);
```

### Swap KLAY to KUSDC in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to KUSDC.
Q.klay.exchangeKlayPos ("kusdc", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
