```meta-Currency
```

# Deposit ETH in Compound

In this scenario, you will borrow ETH in Compound.

### Deposit amount

- Type the amount of asset to deposit.

```input ETH
// ETH to deposit
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(getBalance () >= amountIn, "Insufficient ETH");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.compound.deposit ("ether", amountIn);
```

### Set your deposit as collateral

- This step enables your deposit to be set as a collateral.
- You can borrow assets from Compound if you set your deposit as collateral.
- This step is optional. You may change collateral activation settings in [Compound](https://app.compound.finance/).

```taster
Q.compound.setUseReserveAsCollateral("ether", true);
```

### All steps are done successfully.

- Check your ETH balance in [Compound](https://app.compound.finance/) and your connected wallet.
