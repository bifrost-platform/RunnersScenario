```meta-Currency
```

# Earn KLAY in BiFi X

In this scenario, you will start yield farming(Earn) after leveraging KLAY at the maximum boost in BiFi-X.

### Set amount of KLAY to use.

```input KLAY
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= getBalance (), "Insufficient KLAY");
```

### Leverage KLAY to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of KLAY to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("klay");

// Start Earn position
let ok = Q.bifiX.earn("klay", amount, maxBoost);
assert(ok, "BiFi X is not available at the moment. Please try later.");
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
