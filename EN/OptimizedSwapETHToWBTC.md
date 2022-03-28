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
let outputs = Q.optimizedSwap.eth.getOutputs("wbtc", 1 ether);
let target = Q.optimizedSwap.getBest (outputs);
Q.optimizedSwap.printOutputs (outputs);
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
Q.optimizedSwap.eth.getOutput (target, "wbtc", amountIn);
```

### ChainRunner Q swaps ETH to WBTC in the most optimzed DEX.

- Use slippage (0.5%)

```taster
// Swap ETH to WBTC.
Q.optimizedSwap.eth.swap (target, "wbtc", amountIn);
```

### All steps are done successfully.

- Check your balance in your connected wallet.
