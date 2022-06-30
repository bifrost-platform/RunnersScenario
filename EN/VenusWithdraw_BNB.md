```meta-Currency
```

# Withdraw BNB from Venus

In this scenario, you will withdraw BNB in Venus.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.
- Value shown may not be accurate. or precise value, please obtain asset directly from [Venus](https://app.venus.io/dashboard).

```output-Dynamic
let amountWithdrawMax = Q.venus.getWithdrawableAmount("bnb");
assert(amountWithdrawMax > 0.000001 bnb, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input BNB
// Amount of BNB to withdraw
let amountWithdraw = 1.0;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value.");
assert(amountWithdrawMax >= amountWithdraw, "Insufficient BNB.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.venus.withdraw("bnb", amountWithdraw);
```

### All steps are done successfully.

- Check your BNB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
