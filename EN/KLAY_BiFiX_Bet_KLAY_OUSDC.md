```meta-Currency
```

# Start a long position with KLAY in BiFi X

In this scenario, you will leverage KLAY at maximum boost in BiFi X to easily start a long position with oUSDC.

### Enter the amount of KLAY to leverage at maximum boost.

```input KLAY
let amount = 0.1;
```

```input-Verify
assert(isCurrency (amount), "Invalid valuse");
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(amount <= getBalance(), "Insufficient balance.");
assert(Q.bifiX.isBetLiquidityEnough("klay", "ousdc", amount, Q.bifiX.getMaxBoost("klay")), "Not enough liquidity. Decrease amount.");
```

### Start a long position in BiFi X after leveraging KLAY at maximum boost.

- Use slippage (0.5%)

```taster
// Confirm the maximum boost of oUSDC to leverage in BiFi X.
let maxBoost = L2Lending.bifiX.getMaxBoost ("klay");

// Start position at maximum boost.
let ok = Q.bifiX.bet("klay", "ousdc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi X](https://x.bifi.finance/)
