```meta-Currency
ousdt
```

# Earn oUSDT in BiFi-X

In this scenario, you will start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of oUSDT to use.

- Please check your deposit of oUSDT and enter the amount to use.
- If you do not have any deposit of oUSDT, use the **Buy Tokens** menu.

```input oUSDT
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= Q.Token.balanceOf ("ousdt"), "Insufficient oUSDT.");
```

### Leverage oUSDT to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of oUSDT to leverage in BiFi-X.
let maxBoost = L2Lending.bifiX.getMaxBoost ("ousdt");

// Approve oUSDT before starting position.
Q.bifiX.approve("ousdt", amount);

// Start Earn position
let ok = Q.bifiX.earn("ousdt", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
