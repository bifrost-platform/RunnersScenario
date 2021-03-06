```meta-Currency
```

# Move ETH from Aave V2 to BiFi

In this scenario, you will move ETH from Aave V2 to BiFi. This service may be limited according to the status of Aave V2.

### Confirm the amount of ETH in AAVE v2

- Please be sure to confirm the deposited amount of ETH before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("eth"), "Withdrawal is limited to the circuit status of the market.");
// Confirm the amount of ETH in Aave V2.
let assetAmount = Q.aaveV2.getDepositedAmount ("eth");
assert (assetAmount >= 0.000001 ether, "Confirm the amount of ETH in AAVE v2.");
print ("Deposited ETH:" + assetAmount.toString());
```

### Withdraw ETH in AAVE v2.

```taster
// Withdraw ETH in AAVE.
Q.aaveV2.withdraw ("eth", assetAmount);
```

### Deposit ETH to BiFi.

```taster
// Deposit ETH in BiFi.
Q.bifi.deposit ("eth", assetAmount);
print (assetAmount.toString () + " moved from Aave V2 to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
