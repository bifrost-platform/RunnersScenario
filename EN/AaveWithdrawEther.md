```meta-Currency
```

# Withdraw ETH from Aave V2

In this scenario, you will withdraw ETH from Aave V2. This service may be limited according to the status of Aave V2.

### Confirm asset available to withdraw

- Value shown may not be accurate. or precise value, please obtain asset directly from [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("eth"), "Withdrawal is limited to the circuit status of the market.");
let amountWithdrawMax = Q.aaveV2.getWithdrawableAmount("eth");
assert(amountWithdrawMax > 0.000001 eth, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input ETH
// Amount of ETH to withdraw
let amountOut = 0.1;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut), "Invalid value");
assert(amountWithdrawMax >= amountOut, "Insufficient ETH.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.aaveV2.withdraw("eth", amountOut);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
