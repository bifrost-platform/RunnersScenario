```meta-Currency
keth
```

# Swap KLAY to KETH in KLAYswap

In this scenario, you will swap KLAY to KETH.

### Set the amount of KLAY to swap.

- The amount of KETH available with your KLAY will be automatically calculated.
- Only the maximum amount of KETH available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient. (KLAY will be consumed according to the available balance to swap.)

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic KETH
let kethAmount = Q.klay.getAmountsOutFromExactIn("keth", amountIn);
print(kethAmount);
```

### Swap KLAY to KETH in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to KETH.
Q.klay.exchangeKlayPos ("keth", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
