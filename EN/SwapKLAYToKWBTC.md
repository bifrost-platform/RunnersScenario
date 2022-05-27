```meta-Currency
kwbtc
```

# Swap KLAY to KWBTC in KLAYswap

In this scenario, you will swap KLAY to KWBTC.

### Set the amount of KLAY to swap.

- The amount of KWBTC available with your KLAY will be automatically calculated.
- Only the maximum amount of KWBTC available for swap will be displayed if the token pool in DEX (KLAYswap) is insufficient.
- As there is currently no pool for KLAY/KWBTC pair, you will exchange through one of KSP, KETH, or KUSDT tokens.
- ChainRunner Q will automatically choose the swap method for the highest amount of KWBTC in return.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic KWBTC
let (routingToken, kwbtcAmount) = Q.klay.getKWBTCAmountOutFromExactIn (amountIn);
print(kwbtcAmount);
```

### Swap KLAY to KWBTC in KLAYswap.

- Use default KLAYswap slippage (0.5%)

```taster
// Swap KLAY to KWBTC.
Q.klay.exchangeKlayToKWBTCPos (amountIn, routingToken);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
