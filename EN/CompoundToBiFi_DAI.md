```meta-Currency
dai
```

# Move DAI from Compound to BiFi

In this scenario, you will move DAI from Compound to BiFi.

### Confirm DAI in Compound.

- Please be sure to confirm the deposited amount of DAI before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Compound](https://app.compound.finance/).

```output-Dynamic
// Confirm DAI in Compound.
let assetAmount = Q.compound.getWithdrawableAmount ("dai");
assert (assetAmount >= 0.000001 dai, "Confirm the amount of DAI in Compound.");
print ("Deposited DAI:" + assetAmount.toString());
```

### Withdraw DAI in Compound.

```taster
// Withdraw DAI in Compound.
Q.compound.withdraw ("dai", assetAmount);
```

### Deposit DAI to BiFi.

```taster
// Deposit DAI in BiFi.
Q.bifi.deposit ("dai", assetAmount);
print (assetAmount.toString () + " moved from Compound to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
