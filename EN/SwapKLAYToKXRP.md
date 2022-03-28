```meta-Currency
kxrp
```

# Swap KLAY to KXRP in KLAYswap

In this scenario, you will swap KLAY to KXRP.

### Set the amount of KLAY to swap.

- The amount of KXRP available with your KLAY will be automatically calculated.
- Only the maximum amount of KXRP available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient. (KLAY will be consumed according to the available balance to swap.)

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic KXRP
let kxrpAmount = Q.klay.getAmountsOutFromExactIn("kxrp", amountIn);
print(kxrpAmount);
```

### Swap KLAY to KXRP in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to KXRP.
Q.klay.exchangeKlayPos ("kxrp", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
