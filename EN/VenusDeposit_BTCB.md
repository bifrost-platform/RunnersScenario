```meta-Currency
btcb
```

# Deposit BTCB in Venus

In this scenario, you will deposit BTCB in Venus.

### Deposit amount

- Type the amount of asset to deposit.

```input BTCB
// BTCB to deposit
let amountDeposit = 0.01;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value.");
assert(Q.Token.balanceOf("btcb") >= amountDeposit, "Insufficient BTCB");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.venus.deposit("btcb", amountDeposit);
```

### Set your deposit as collateral

- This step enables your deposit to be set as a collateral.
- You can borrow assets from Venus if you set your deposit as collateral.
- This step is optional. You may change collateral activation settings in [Venus](https://app.venus.io/dashboard).

```taster
Q.venus.setUseReserveAsCollateral("btcb", true);
```

### All steps are done successfully.

- Check your BTCB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
