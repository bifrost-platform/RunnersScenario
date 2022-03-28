```meta-Currency
kdai
```

# Swap KLAY to KDAI in KLAYswap

In this scenario, you will swap KLAY to KDAI.

### Set the amount of KLAY to swap.

- The amount of KDAI available with your KLAY will be automatically calculated.
- Only the maximum amount of KDAI available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient. (KLAY will be consumed according to the available balance to swap.)

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic KDAI
let kdaiAmount = Q.klay.getAmountsOutFromExactIn("kdai", amountIn);
print(kdaiAmount);
```

### Swap KLAY to KDAI in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to KDAI.
Q.klay.exchangeKlayPos ("kdai", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
