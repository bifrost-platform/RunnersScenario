```meta-Currency
dai
```

# Swap BNB to DAI in SushiSwap

In this scenario, you will swap BNB to DAI.

### Set the amount of BNB to swap.

- The amount of DAI available with your BNB will be automatically calculated.
- Only the maximum amount of DAI available for swap will be displayed if the token pool in DEX (Sushiswap) is insufficient.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance (), "Insufficient BNB.");
```

```output-Dynamic DAI
let daiAmount = Q.sushi.getAmountsOutFromExactIn("dai", amountIn);
print(daiAmount);
```

### Swap BNB to DAI in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
// Swap BNB to DAI.
Q.sushi.sell ("bnb", "dai", amountIn);
```

### All steps are done successfully.

- Check your balance on the left bar or your connected wallet.
