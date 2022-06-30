```meta-Currency
oeth
```

# Start a long position with oETH in BiFi X

In this scenario, you will leverage oETH at maximum boost in BiFi X to easily start a long position with oUSDC.

### Enter the amount of oETH to leverage at maximum boost.

```input oETH
let amount = 0.1;
```

```input-Verify
assert(isCurrency (amount), "Invalid valuse");
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(amount <= Q.Token.balanceOf ("oeth"), "Insufficient balance.");
assert(Q.bifiX.isBetLiquidityEnough("oeth", "ousdc", amount, Q.bifiX.getMaxBoost("oeth")), "Not enough liquidity. Decrease amount.");
```

### Start a long position in BiFi X after leveraging oETH at maximum boost.

- Use slippage (0.5%)

```taster
// Confirm the maximum boost of oUSDC to leverage in BiFi X.
let maxBoost = L2Lending.bifiX.getMaxBoost ("oeth");

// Confirm the amount of oUSDC to use in BiFI X.
Q.bifiX.approve("oeth", amount);

// Start position at maximum boost.
let ok = Q.bifiX.bet("oeth", "ousdc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi X](https://x.bifi.finance/)
