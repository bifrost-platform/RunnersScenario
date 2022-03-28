```meta-Currency
bifib
```

# Earn BNB in BiFi X

In this scenario, you will start yield farming(Earn) after leveraging BNB at the maximum boost in BiFi-X.

### Confirm BiFi to be used for service fee in BiFi-X.

- To use BiFi-X service, you need to hold BiFi tokens in your wallet to pay for service fee.

```output-Dynamic
let bifiFee = Q.bifiX.getFee ();
let bifiBalance = Q.erc20.balanceOf ("bifib");
assert(bifiBalance >= bifiFee, "Insufficient BNB.");
print ("BiFi tokens needed for service fee: " + bifiFee.toString ());
```

### Set amount of BNB to use.

```input BNB
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value.In");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= getBalance (), "Insufficient BNB");
```

### BiFi-X confirms fee payment of BiFi tokens.

```taster
Q.bifiX.approveBiFi (bifiFee);
```

### Leverage BNB to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of BNB to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("bnb");

// Start Earn position
Q.bifiX.createEarnPosition ("bnb", amount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.

