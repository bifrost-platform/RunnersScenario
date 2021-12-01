```meta-Currency
```

# Withdraw Ether from Aave V2

In this scenario, you will withdraw Ether from Aave V2.

### Confirm asset available to withdraw

- Value shown may not be accurate. or precise value, please obtain asset directly from [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
let amountWithdrawMax = Q.aaveV2.getAmountWithdrawMax("ether");
assert(amountWithdrawMax > 0.000001 ether, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input ETH
// Amount of Ether to withdraw
let amountOut = 0.1;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut), "Invalid value");
assert(amountWithdrawMax >= amountOut, "Insufficient Ether.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.aaveV2.withdraw("ether", amountOut);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
