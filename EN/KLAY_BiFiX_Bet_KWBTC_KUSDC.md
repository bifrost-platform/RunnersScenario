```meta-Currency
kwbtc
```

# Start a long position with KWBTC in BiFi X

In this scenario, you will leverage KWBTC at maximum boost in BiFi X to easily start a long position with KUSDC.

### Enter the amount of KWBTC to leverage at maximum boost.

```input KWBTC
let amount = 0.1;
```

```input-Verify
assert(isCurrency (amount), "Invalid valuse");
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(amount <= Q.Token.balanceOf ("kwbtc"), "Insufficient balance.");
assert(Q.bifiX.isBetLiquidityEnough("kwbtc", "kusdc", amount, Q.bifiX.getMaxBoost("kwbtc")), "Not enough liquidity. Decrease amount.");
```

### Start a long position in BiFi X after leveraging KWBTC at maximum boost.

- Use slippage (0.5%)

```taster
// Confirm the maximum boost of KUSDC to leverage in BiFi X.
let maxBoost = Q.bifiX.getMaxBoost ("kwbtc");

// Confirm the amount of KUSDC to use in BiFI X.
Q.bifiX.approve("kwbtc", amount);

// Start position at maximum boost.
let ok = Q.bifiX.bet("kwbtc", "kusdc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi X](https://x.bifi.finance/)
