```meta-Currency
link
```

# Move LINK from Aave V2 to BiFi

In this scenario, you will move LINK from Aave V2 to BiFi.

### Confirm the amount of LINK in AAVE v2

- Please be sure to confirm the deposited amount of LINK before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
// Confirm the amount of LINK in Aave V2.
let assetAmount = Q.aaveV2.getUserReserve ("link");
assert (assetAmount >= 0.000001 link, "Confirm the amount of LINK in AAVE v2.");
print ("Deposited LINK:" + assetAmount.toString());
```

### Withdraw LINK in AAVE v2.

```taster
Withdraw LINK in AAVE.
Q.aaveV2.withdraw ("link", assetAmount);
```

### Deposit LINK to BiFi.

```taster
// Deposit LINK in BiFi.
bifi.token.deposit ("link", assetAmount);
print (assetAmount.toString () + " moved from Aave V2 to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
