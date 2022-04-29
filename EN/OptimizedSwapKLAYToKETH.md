```meta-Currency
keth
```

# Swap KLAY to KETH

ChainRunner Q compares DEXes to swap KLAY to KETH in the most price efficient way.

### ChainRunner Q finds the most optimzed DEX to proceed this scenario.

- ChainRunner finds the most optimzed DEX to swap the most quantity of tokens.
- In this step, the exchangeable number of tokens per DEX is shown based on 1 KLAY.
- Only the maximum amount of KETH available for swap will be displayed if the token pool in DEX is insufficient.

```output-Dynamic
let outputs = Q.optimizedSwap.klay.getOutputs("keth", 1 klay);
let target = Q.optimizedSwap.getBest (outputs);
let (bestAmount, target) = outputs[0];
print("Best DEX is " + target + ". (" + bestAmount.toString() + ")\n");
print ("\nDifferences from Best DEX\n");
print ("\nCurrent Chain : \n");
Q.optimizedSwap.printOutputs (bestAmount, outputs);
print ("\nOther Chain : ");
Q.optimizedSwap.klay.printOtherChainOutputs (bestAmount, "keth", 1 klay);
```

### Set the amount of KLAY to swap.

- The amount of KETH available with your KLAY will calculated automatically.
- Only KLAY used for the actual purchase will be consumed.

```input-Dynamic KLAY
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value.");
assert(amountIn <= getBalance(), "Insufficient KLAY.");
```

```output-Dynamic KETH
Q.optimizedSwap.klay.getOutput (target, "keth", amountIn);
```

### ChainRunner Q swaps KLAY to KETH in the most optimzed DEX.

- Use slippage (0.5%)

```taster
// Swap KLAY to KETH.
Q.optimizedSwap.klay.swap (target, "keth", amountIn);
```

### All steps are done successfully.

- Check your balance in your connected wallet.
