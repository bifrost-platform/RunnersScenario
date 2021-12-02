```meta-Currency
usdt
```

# Deposit USDT in Venus

In this scenario, you will deposit USDT in Venus.

### Deposit amount

- Type the amount of asset to deposit.

```input USDT
// USDT to deposit
let amountDeposit = 100;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value.");
assert(Q.erc20.balanceOf("usdt") >= amountDeposit, "Insufficient USDT");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.venus.deposit("usdt", amountDeposit);
```

### Set your deposit as collateral

- This step enables your deposit to be set as a collateral.
- You can borrow assets from Venus if you set your deposit as collateral.
- This step is optional. You may change collateral activation settings in [Venus](https://app.venus.io/dashboard).

```taster
Q.venus.setUseReserveAsCollateral("usdt", true);
```

### All steps are done successfully.

- Check your USDT balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
