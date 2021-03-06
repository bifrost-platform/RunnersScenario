```meta-Currency
usdt
```

# Move USDT from Aave V2 to BiFi

In this scenario, you will move USDT from Aave V2 to BiFi. This service may be limited according to the status of Aave V2.

### Confirm the amount of USDT in AAVE v2

- Please be sure to confirm the deposited amount of USDT before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("usdt"), "Withdrawal is limited to the circuit status of the market.");
// Confirm the amount of USDT in Aave V2.
let assetAmount = Q.aaveV2.getDepositedAmount ("usdt");
assert (assetAmount >= 0.000001 usdt, "Confirm the amount of USDT in AAVE v2.");
print ("Deposited USDT:" + assetAmount.toString());
```

### Withdraw USDT in AAVE v2.

```taster
// Withdraw USDT in AAVE.
Q.aaveV2.withdraw ("usdt", assetAmount);
```

### Deposit USDT to BiFi.

```taster
// Deposit USDT in BiFi.
Q.bifi.deposit ("usdt", assetAmount);
print (assetAmount.toString () + " moved from Aave V2 to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
