```meta-Currency
usdc
```

# Move USDC from Aave V2 to BiFi

In this scenario, you will move USDC from Aave V2 to BiFi. This service may be limited according to the status of Aave V2.

### Confirm the amount of USDC in AAVE v2

- Please be sure to confirm the deposited amount of USDC before you go on to the next step.
- If you are using deposits as collateral, withdrawals may be limited. Check availability in [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(Q.aaveV2.getIsActive("usdc"), "Withdrawal is limited to the circuit status of the market.");
// Confirm the amount of USDC in Aave V2.
let assetAmount = Q.aaveV2.getUserReserve ("usdc");
assert (assetAmount >= 0.000001 usdc, "Confirm the amount of USDC in AAVE v2.");
print ("Deposited USDC:" + assetAmount.toString());
```

### Withdraw USDC in AAVE v2.

```taster
// Withdraw USDC in AAVE.
Q.aaveV2.withdraw ("usdc", assetAmount);
```

### Deposit USDC to BiFi.

```taster
// Deposit USDC in BiFi.
Q.bifi.deposit ("usdc", assetAmount);
print (assetAmount.toString () + " moved from Aave V2 to BiFi.");
```

### All steps are done successfully.

- Confirm your status in [BiFi](https://app.bifi.finance/lend?chainid=mainnet)
