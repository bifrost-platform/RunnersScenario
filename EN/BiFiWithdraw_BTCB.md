```meta-Currency
btcb
```

# Withdraw BTCB from BiFi

In this scenario, you will withdraw BTCB in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getMaxWithdrawAmount("btcb");
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
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getMaxWithdrawAmount("btcb") >= amountWithdraw, "Insufficient BTCB to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("btcb", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn BTCB in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
