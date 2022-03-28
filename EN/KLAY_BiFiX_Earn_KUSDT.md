```meta-Currency
kusdt
```

# Earn KUSDT in BiFi-X

In this scenario, you will start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of KUSDT to use.

- Please check your deposit of KUSDT and enter the amount to use.
- If you do not have any deposit of KUSDT, use the **Buy Tokens** menu.

```input KUSDT
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= Q.Token.balanceOf ("kusdt"), "Insufficient KUSDT.");
```

### Leverage KUSDT to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of KUSDT to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("kusdt");

// Approve KUSDT before starting position.
Q.bifiX.approve("kusdt", amount);

// Start Earn position
let ok = Q.bifiX.earn("kusdt", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
