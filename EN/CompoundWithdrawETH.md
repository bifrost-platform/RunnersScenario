```meta-Currency
```

# Withdraw ETH from Compound

In this scenario, you will withdraw ETH in Compound.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.
- Value shown may not be accurate. or precise value, please obtain asset directly from [Compound](https://app.compound.finance/).

```output-Dynamic
let amountDepositMax = Q.compound.getDepositAssetAmount ("ether");
assert(amountDepositMax >= 0.000001 ether,"Insufficient asset to withdraw.");
print ("Asset available to withdraw: " + amountDepositMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input ETH
// Amount of ETH to withdraw
let amountOut = 0.1;
```

```input-Verify
assert(amountOut > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountOut));
assert(amountDepositMax >= amountOut, "Insufficient ETH.");
```

### Proceed withdrawal

- Now, proceed withdrawal.

```taster
Q.compound.withdraw ("ether", amountOut);
```

### All steps are done successfully.

- Check your ETH balance in [Compound](https://app.compound.finance/) and your connected wallet.
