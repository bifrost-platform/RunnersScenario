```meta-Currency
dai
```

# Swap BNB to DAI

ChainRunner Q compares DEXes to swap BNB to DAI in the most price efficient way.

### ChainRunner Q finds the most optimzed DEX to proceed this scenario.

- ChainRunner finds the most optimzed DEX to swap the most quantity of tokens.
- In this step, the exchangeable number of tokens per DEX is shown based on 1 BNB.
- Only the maximum amount of DAI available for swap will be displayed if the token pool in DEX is insufficient.

```output-Dynamic
let outputs = Q.optimizedSwap.bsc.getOutputs("dai", 1 bnb);
let target = Q.optimizedSwap.getBest (outputs);
Q.optimizedSwap.printOutputs (outputs);
```

### Set the amount of BNB to swap.

- The amount of DAI available with your BNB will calculated automatically.
- Only BNB used for the actual purchase will be consumed.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value.");
assert(amountIn <= getBalance(), "Insufficient BNB.");
```

```output-Dynamic DAI
Q.optimizedSwap.bsc.getOutput (target, "dai", amountIn);
```

### ChainRunner Q swaps BNB to DAI in the most optimzed DEX.

- Use slippage (0.5%)

```taster
// Swap BNB to DAI.
Q.optimizedSwap.bsc.swap (target, "dai", amountIn);
```

### All steps are done successfully.

- Check your balance in your connected wallet.