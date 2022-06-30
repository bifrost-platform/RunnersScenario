```meta-Currency
wbtc
```

# Swap ETH to WBTC

ChainRunner Q compares DEXes to swap ETH to WBTC in the most price efficient way.

### ChainRunner Q finds the most optimzed DEX to proceed this scenario.

- ChainRunner finds the most optimzed DEX to swap the most quantity of tokens.
- In this step, the exchangeable number of tokens per DEX is shown based on 1 Ethereum.
- Only the maximum amount of WBTC available for swap will be displayed if the token pool in DEX is insufficient.

```output-Dynamic
let outputs = Q.optimizedSwap.getAmountOuts("eth", "wbtc", 1 eth);
Q.optimizedSwap.checkOutputs (outputs);
let (bestAmount, target) = outputs[0];
print("Best DEX is " + target + ". (" + bestAmount.toString() + ")\n");
print ("\nDifferences from Best DEX\n");
print ("\nCurrent Chain : \n");
Q.optimizedSwap.printOutputs (bestAmount, outputs);
print ("\nOther Chain : ");
Q.optimizedSwap.printOtherOutputs (bestAmount, "eth", "wbtc", 1 eth);
```

### Set the amount of ETH to swap.

- The amount of WBTC available with your ETH will calculated automatically.
- Only ETH used for the actual purchase will be consumed.

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value.");
assert(amountIn <= getBalance(), "Insufficient ETH.");
```

```output-Dynamic WBTC
Q.optimizedSwap.getAmountOut (target, "eth", "wbtc", amountIn);
```

### ChainRunner Q swaps ETH to WBTC in the most optimzed DEX.

- Use slippage (0.5%)

```taster
// Swap ETH to WBTC.
Q.optimizedSwap.swap (target, "eth", "wbtc", amountIn);
```

### All steps are done successfully.

- Check your balance in your connected wallet.
