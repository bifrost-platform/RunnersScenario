```meta-Currency
usdt
```

# Move USDT from Compound to BiFi

In this scenario, you will move USDT from Compound to BiFi.

### Confirm USDT in Compound.

- Please be sure to confirm the deposited amount of USDT before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Compound](https://app.compound.finance/).

```output-Dynamic
// Confirm USDT in Compound.
let assetAmount = Q.compound.getDepositAssetAmount ("usdt");
assert (assetAmount >= 0.000001 usdt, "Confirm the amount of USDT in Compound.");
print ("Deposited USDT:" + assetAmount.toString());
```

### Withdraw USDT in Compound.

```taster
// Withdraw USDT in Compound.
Q.compound.withdraw ("usdt", assetAmount);
```

### Deposit USDT to BiFi.

```taster
// Deposit USDT in BiFi.
Q.bifi.deposit ("usdt", assetAmount);
print (assetAmount.toString () + " moved from Compound to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
