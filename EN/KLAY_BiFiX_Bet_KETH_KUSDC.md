```meta-Currency
keth
```

# Start a long position with KETH in BiFi X

In this scenario, you will leverage KETH at maximum boost in BiFi X to easily start a long position with KUSDC.

### Enter the amount of KETH to leverage at maximum boost.

```input KETH
let amount = 0.1;
```

```input-Verify
assert(isCurrency (amount), "Invalid valuse");
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(amount <= Q.Token.balanceOf ("keth"), "Insufficient balance.");
assert(Q.bifiX.isBetLiquidityEnough("keth", "kusdc", amount, Q.bifiX.getMaxBoost("keth")), "Not enough liquidity. Decrease amount.");
```

### Start a long position in BiFi X after leveraging KETH at maximum boost.

- Use slippage (0.5%)

```taster
// Confirm the maximum boost of KUSDC to leverage in BiFi X.
let maxBoost = Q.bifiX.getMaxBoost ("keth");

// Confirm the amount of KUSDC to use in BiFI X.
Q.bifiX.approve("keth", amount);

// Start position at maximum boost.
let ok = Q.bifiX.bet("keth", "kusdc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi X](https://x.bifi.finance/)
