```meta-Currency
usdt
```

# Withdraw USDT from Aave V2

In this scenario, you will withdraw USDT from Aave V2. This service may be limited according to the status of Aave V2.

### Confirm asset available to withdraw

- Value shown may not be accurate. or precise value, please obtain asset directly from [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("usdt"), "Withdrawal is limited to the circuit status of the market.");
let amountWithdrawMax = Q.aaveV2.getWithdrawableAmount("usdt");
assert(amountWithdrawMax > 0.000001 usdt, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input USDT
// Amount of USDT to withdraw
let amountOut = 100;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut), "Invalid value");
assert(amountWithdrawMax >= amountOut, "Insufficient USDT.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.aaveV2.withdraw("usdt", amountOut);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
