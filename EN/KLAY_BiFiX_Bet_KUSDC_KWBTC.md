```meta-Currency
kusdc
```

# Start a short position with KUSDC in BiFi X

In this scenario, you will leverage KUSDC at maximum boost in BiFi X to easily start short positions with KWBTC.

### Enter the amont of KUSDC to leverage at maximum boost.

```input KUSDC
let amount = 100;
```

```input-Verify
assert(isCurrency (amount), "Invalid value.");
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(amount <= Q.Token.balanceOf ("kusdc"), "Insufficient balance.");
assert(Q.bifiX.isBetLiquidityEnough("kusdc", "kwbtc", amount, Q.bifiX.getMaxBoost("kusdc")), "Not enough liquidity. Decrease amount.");
```

### Start a short position in BiFi X after leveraging KUSDC at maximum boost.

- Use slippage (0.5%)

```taster
// Confirm the maximum boost of KUSDC to leverage in BiFi X.
let maxBoost = Q.bifiX.getMaxBoost ("kusdc");

// Confirm the amount of KUSDC to use in BiFI X.
Q.bifiX.approve("kusdc", amount);

// Start position at maximum boost.
let ok = Q.bifiX.bet("kusdc", "kwbtc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi X](https://x.bifi.finance/)
