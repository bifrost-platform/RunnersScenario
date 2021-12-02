```meta-Currency
btcb
```

# Withdraw BTCB from Venus

In this scenario, you will withdraw BTCB in Venus.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.
- Value shown may not be accurate. or precise value, please obtain asset directly from [Venus](https://app.venus.io/dashboard).

```output-Dynamic
let amountWithdrawMax = Q.venus.getAmountWithdrawMax("btcb");
assert(amountWithdrawMax > 0.000001 btcb, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input BTCB
// Amount of BTCB to withdraw
let amountWithdraw = 0.01;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value.");
assert(amountWithdrawMax >= amountWithdraw, "Insufficient BTCB.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.venus.withdraw("btcb", amountWithdraw);
```

### All steps are done successfully.

- Check your BTCB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
