```meta-Currency
owbtc
```

# Earn oWBTC in BiFi-X

In this scenario, you will start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of oWBTC to use.

- Please check your deposit of oWBTC and enter the amount to use.
- If you do not have any deposit of oWBTC, use the **Buy Tokens** menu.

```input oWBTC
let amount = 0.001;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= Q.Token.balanceOf ("owbtc"), "Insufficient oWBTC.");
```

### Leverage oWBTC to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of oWBTC to leverage in BiFi-X.
let maxBoost = L2Lending.bifiX.getMaxBoost ("owbtc");

// Approve oWBTC before starting position.
Q.bifiX.approve("owbtc", amount);

// Start Earn position
let ok = Q.bifiX.earn("owbtc", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
