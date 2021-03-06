```meta-Currency
wbtc
```

# Withdraw WBTC from Aave V2

In this scenario, you will withdraw WBTC from Aave V2. This service may be limited according to the status of Aave V2.

### Confirm asset available to withdraw

- Value shown may not be accurate. or precise value, please obtain asset directly from [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("wbtc"), "Withdrawal is limited to the circuit status of the market.");
let amountWithdrawMax = Q.aaveV2.getWithdrawableAmount("wbtc");
assert(amountWithdrawMax > 0.000001 wbtc, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input WBTC
// Amount of WBTC to withdraw
let amountOut = 0.01;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut), "Invalid value");
assert(amountWithdrawMax >= amountOut, "Insufficient WBTC.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.aaveV2.withdraw("wbtc", amountOut);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
