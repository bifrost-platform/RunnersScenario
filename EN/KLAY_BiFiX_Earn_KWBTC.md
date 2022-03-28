```meta-Currency
kwbtc
```

# Earn KWBTC in BiFi-X

In this scenario, you will start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of KWBTC to use.

- Please check your deposit of KWBTC and enter the amount to use.
- If you do not have any deposit of KWBTC, use the **Buy Tokens** menu.

```input KWBTC
let amount = 0.001;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= Q.Token.balanceOf ("kwbtc"), "Insufficient KWBTC.");
```

### Leverage KWBTC to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of KWBTC to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("kwbtc");

// Approve KWBTC before starting position.
Q.bifiX.approve("kwbtc", amount);

// Start Earn position
let ok = Q.bifiX.earn("kwbtc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
