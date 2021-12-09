```meta-Currency
wbtc
```

# Withdraw WBTC from Compound

In this scenario, you will withdraw WBTC in Compound.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.
- Value shown may not be accurate. or precise value, please obtain asset directly from [Compound](https://app.compound.finance/).

```output-Dynamic
let amountWithdrawMax = Q.compound.getDepositAssetAmount ("wbtc");
assert(amountWithdrawMax >= 0.000001 wbtc,"Insufficient asset to withdraw.");
print ("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input WBTC
// Amount of WBTC to withdraw
let amountOut = 0.01;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut));
assert(amountWithdrawMax >= amountOut, "Insufficient WBTC.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.compound.withdraw ("wbtc", amountOut);
```

### All steps are done successfully.

- Check your WBTC balance in [Compound](https://app.compound.finance/) and your connected wallet.
