```meta-Currency
usdt
```

# Withdraw USDT from Compound

In this scenario, you will withdraw USDT in Compound.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.
- Value shown may not be accurate. or precise value, please obtain asset directly from [Compound](https://app.compound.finance/).

```output-Dynamic
let amountWithdrawMax = Q.compound.getWithdrawableAmount ("usdt");
assert(amountWithdrawMax >= 0.000001 usdt,"Insufficient asset to withdraw.");
print ("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input USDT
// Amount of USDT to withdraw
let amountOut = 100;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut));
assert(amountWithdrawMax >= amountOut, "Insufficient USDT.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.compound.withdraw ("usdt", amountOut);
```

### All steps are done successfully.

- Check your USDT balance in [Compound](https://app.compound.finance/) and your connected wallet.
