```meta-Currency
ousdc
```

# Start a short position with oUSDC in BiFi X

In this scenario, you will leverage oUSDC at maximum boost in BiFi X to easily start short positions with oETH.

### Enter the amont of oUSDC to leverage at maximum boost.

```input oUSDC
let amount = 100;
```

```input-Verify
assert(isCurrency (amount), "Invalid value.");
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(amount <= Q.Token.balanceOf ("ousdc"), "Insufficient balance.");
assert(Q.bifiX.isBetLiquidityEnough("ousdc", "oeth", amount, Q.bifiX.getMaxBoost("ousdc")), "Not enough liquidity. Decrease amount.");
```

### Start a short position in BiFi X after leveraging oUSDC at maximum boost.

- Use slippage (0.5%)

```taster
// Confirm the maximum boost of oUSDC to leverage in BiFi X.
let maxBoost = L2Lending.bifiX.getMaxBoost ("ousdc");

// Confirm the amount of oUSDC to use in BiFI X.
Q.bifiX.approve("ousdc", amount);

// Start position at maximum boost.
let ok = Q.bifiX.bet("ousdc", "oeth", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi X](https://x.bifi.finance/)
