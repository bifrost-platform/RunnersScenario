```meta-Currency
ousdt
```

# Swap KLAY to oUSDT

ChainRunner Q compares DEXes to swap KLAY to oUSDT in the most price efficient way.

### ChainRunner Q finds the most optimzed DEX to proceed this scenario.

- ChainRunner finds the most optimzed DEX to swap the most quantity of tokens.
- In this step, the exchangeable number of tokens per DEX is shown based on 1 KLAY.
- Only the maximum amount of oUSDT available for swap will be displayed if the token pool in DEX is insufficient.

```output-Dynamic
let outputs = Q.optimizedSwap.getAmountOuts("klay", "ousdt", 1 klay);
Q.optimizedSwap.checkOutputs (outputs);
let (bestAmount, target) = outputs[0];
print("Best DEX is " + target + ". (" + bestAmount.toString() + ")\n");
print ("\nDifferences from Best DEX\n");
print ("\nCurrent Chain : \n");
Q.optimizedSwap.printOutputs (bestAmount, outputs);
print ("\nOther Chain : ");
Q.optimizedSwap.printOtherOutputs (bestAmount, "klay", "ousdt", 1 klay);
```

### Set the amount of KLAY to swap.

- The amount of oUSDT available with your KLAY will calculated automatically.
- Only KLAY used for the actual purchase will be consumed.

```input-Dynamic KLAY
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value.");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic oUSDT
Q.optimizedSwap.getAmountOut (target, "klay", "ousdt", amountIn);
```

### ChainRunner Q swaps KLAY to oUSDT in the most optimzed DEX.

- Use slippage (0.5%)

```taster
// Swap KLAY to oUSDT.
Q.optimizedSwap.swap (target, "klay", "ousdt", amountIn);
```

### All steps are done successfully.

- Check your balance in your connected wallet.