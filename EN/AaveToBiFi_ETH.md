```meta-Currency
```

# Move ETH from Aave V2 to BiFi

In this scenario, you will move ETH from Aave V2 to BiFi.

### Confirm the amount of ETH in AAVE v2

- Please be sure to confirm the deposited amount of ETH before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
// Confirm the amount of ETH in Aave V2.
let assetAmount = Q.aaveV2.getUserReserve ("ether");
assert (assetAmount >= 0.000001 ether, "Confirm the amount of ETH in AAVE v2.");
print ("Deposited ETH:" + assetAmount.toString());
```

### Withdraw ETH in AAVE v2.

```taster
Withdraw ETH in AAVE.
Q.aaveV2.withdraw ("ether", assetAmount);
```

### Deposit ETH to BiFi.

```taster
// Deposit ETH in BiFi.
bifi.eth.deposit (assetAmount);
print (assetAmount.toString () + " moved from Aave V2 to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
