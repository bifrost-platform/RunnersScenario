```meta-Currency
```

# Deposit BNB in Venus

In this scenario, you will deposit BNB in Venus.

### Deposit amount

- Type the amount of asset to deposit.

```input BNB
// BNB to deposit
let amountDeposit = 1.0;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value.");
assert(getBalance() >= amountDeposit, "Insufficient BNB");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.venus.deposit("bnb", amountDeposit);
```

### Set your deposit as collateral

- This step enables your deposit to be set as a collateral.
- You can borrow assets from Venus if you set your deposit as collateral.
- This step is optional. You may change collateral activation settings in [Venus](https://app.venus.io/dashboard).

```taster
Q.venus.setUseReserveAsCollateral("bnb", true);
```

### All steps are done successfully.

- Check your BNB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
