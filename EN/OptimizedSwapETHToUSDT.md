```meta-Currency
usdt
```

# Swap ETH to USDT

ChainRunner Q compares DEXes to swap ETH to USDT in the most price efficient way.

### ChainRunner Q finds the most optimzed DEX to proceed this scenario.

- ChainRunner finds the most optimzed DEX to swap the most quantity of tokens.
- In this step, the exchangeable number of tokens per DEX is shown based on 1 Ethereum.
- Only the maximum amount of USDT available for swap will be displayed if the token pool in DEX is insufficient.

```output-Dynamic
let outputs = Q.optimizedSwap.eth.getOutputs("usdt", 1 ether);
let target = Q.optimizedSwap.getBest (outputs);
let (bestAmount, target) = outputs[0];
print("Best DEX is " + target + ". (" + bestAmount.toString() + ")\n");
print ("\nDifferences from Best DEX\n");
print ("\nCurrent Chain : \n");
Q.optimizedSwap.printOutputs (bestAmount, outputs);
print ("\nOther Chain : ");
Q.optimizedSwap.eth.printOtherChainOutputs (bestAmount, "usdt", 1 ether);
```

### Set the amount of ETH to swap.

- The amount of USDT available with your ETH will calculated automatically.
- Only ETH used for the actual purchase will be consumed.

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value.");
assert(amountIn <= getBalance(), "Insufficient ETH.");
```

```output-Dynamic USDT
Q.optimizedSwap.eth.getOutput (target, "usdt", amountIn);
```

### ChainRunner Q swaps ETH to USDT in the most optimzed DEX.

- Use slippage (0.5%)

```taster
// Swap ETH to USDT.
Q.optimizedSwap.eth.swap (target, "usdt", amountIn);
```

### All steps are done successfully.

- Check your balance in your connected wallet.
