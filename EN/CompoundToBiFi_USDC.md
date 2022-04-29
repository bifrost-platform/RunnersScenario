```meta-Currency
usdc
```

# Move USDC from Compound to BiFi

In this scenario, you will move USDC from Compound to BiFi.

### Confirm USDC in Compound.

- Please be sure to confirm the deposited amount of USDC before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Compound](https://app.compound.finance/).

```output-Dynamic
// Confirm USDC in Compound.
let assetAmount = Q.compound.getDepositAssetAmount ("usdc");
assert (assetAmount >= 0.000001 usdc, "Confirm the amount of USDC in Compound.");
print ("Deposited USDC:" + assetAmount.toString());
```

### Withdraw USDC in Compound.

```taster
// Withdraw USDC in Compound.
Q.compound.withdraw ("usdc", assetAmount);
```

### Deposit USDC to BiFi.

```taster
// Deposit USDC in BiFi.
Q.bifi.deposit ("usdc", assetAmount);
print (assetAmount.toString () + " moved from Compound to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
