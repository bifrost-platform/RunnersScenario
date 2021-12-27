```meta-Currency
```

# Move ETH from Compound to BiFi

In this scenario, you will move ETH from Compound to BiFi.

### Confirm ETH in Compound.

- Please be sure to confirm the deposited amount of ETH before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Compound](https://app.compound.finance/).

```output-Dynamic
// Confirm ETH in Compound.
let assetAmount = Q.compound.getDepositAssetAmount ("ether");
assert (assetAmount >= 0.000001 ether, "Confirm the amount of ETH in Compound.");
print ("Deposited ETH:" + assetAmount.toString());
```

### Withdraw ETH in Compound.

```taster
// Withdraw ETH in Compound.
Q.compound.withdraw ("ether", assetAmount);
```

### Deposit ETH to BiFi.

```taster
// Deposit ETH in BiFi.
bifi.coin.deposit (assetAmount);
print (assetAmount.toString () + " moved from Compound to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
