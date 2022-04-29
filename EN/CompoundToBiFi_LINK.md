```meta-Currency
link
```

# Move LINK from Compound to BiFi

In this scenario, you will move LINK from Compound to BiFi.

### Confirm the amount of LINK in Compound

- Please be sure to confirm the deposited amount of LINK before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Compound](https://app.compound.finance/).

```output-Dynamic
// Confirm LINK in Compound.
let assetAmount = Q.compound.getDepositAssetAmount ("link");
assert (assetAmount >= 0.000001 link, "Confirm the amount of LINK in Compound.");
print ("Deposited LINK:" + assetAmount.toString());
```

### Withdraw LINK in Compound.

```taster
// Withdraw LINK in Compound.
Q.compound.withdraw ("link", assetAmount);
```

### Deposit LINK to BiFi.

```taster
// Deposit LINK in BiFi.
Q.bifi.deposit ("link", assetAmount);
print (assetAmount.toString () + " moved from Compound to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
