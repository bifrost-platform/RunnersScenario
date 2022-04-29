```meta-Currency
dai
```

# Move DAI from Aave V2 to BiFi

In this scenario, you will move DAI from Aave V2 to BiFi. This service may be limited according to the status of Aave V2.

### Confirm the amount of DAI in AAVE v2

- Please be sure to confirm the deposited amount of DAI before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(Q.aaveV2.getIsActive("dai"), "Withdrawal is limited to the circuit status of the market.");
// Confirm the amount of DAI in Aave V2.
let assetAmount = Q.aaveV2.getUserReserve ("dai");
assert(assetAmount >= 0.000001 dai, "Confirm the amount of DAI in AAVE v2.");
print ("Deposited DAI:" + assetAmount.toString());
```

### Withdraw DAI in AAVE v2.

```taster
// Withdraw DAI in AAVE.
Q.aaveV2.withdraw ("dai", assetAmount);
```

### Deposit DAI to BiFi.

```taster
// Deposit DAI in BiFi.
Q.bifi.deposit ("dai", assetAmount);
print (assetAmount.toString () + " moved from Aave V2 to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
