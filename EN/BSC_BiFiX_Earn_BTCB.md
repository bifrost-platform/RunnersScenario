```meta-Currency
bifib, btcb
```

# Earn BTCB in BiFi-X

In this scenario, you will start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Confirm BiFi to be used for service fee in BiFi-X.

- To use BiFi-X service, you need to hold BiFi tokens in your wallet to pay for service fee.

```output-Dynamic
let bifiFee = Q.bifiX.getFee ();
let bifiBalance = Q.Token.balanceOf ("bifib");
assert(bifiBalance >= bifiFee, "Insufficient BiFi");
print ("BiFi tokens needed for service fee: " + bifiFee.toString ());
```

### Set amount of BTCB to use.

- Please check your deposit of BTCB and enter the amount to use.
- If you do not have any deposit of BTCB, use the **Buy Tokens** menu.

```input BTCB
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= Q.Token.balanceOf ("btcb"), "Insufficient BTCB." );
```

### Confirm BiFi to be used for service fee in BiFi-X.

```taster
Q.bifiX.approve("bifib", bifiFee);
```

### Leverage BTCB to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of BTCB to leverage in BiFi-X.
let maxBoost = L2Lending.bifiX.getMaxBoost ("btcb");

// Approve BTCB before starting position.
Q.bifiX.approve("btcb", amount);

// Start Earn position
Q.bifiX.earn("btcb", amount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
