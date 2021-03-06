```meta-Currency
```

# Deposit ETH in Aave V2

In this scenario, you will deposit ETH in Aave V2. This service may be limited according to the status of Aave V2.

### Deposit amount

- Type the amount of asset to deposit.

```input ETH
// Number of ETH to deposit
let amountIn = 0.1;
```

```input-Verify
assert(L2Lending.aaveV2.getIsActive("eth") && !L2Lending.aaveV2.getIsFrozen("eth"), "Deposit is limited due to the circuit status of the market.");
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(getBalance() >= amountIn, "Insufficient number of ETH");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.aaveV2.deposit("eth", amountIn);
```

### Set your deposit as collateral

- This step enables your deposit to be set as a collateral.

- You can borrow assets from Aave V2 if you set your deposit as collateral.
- This step is optional. You may change collateral activation settings in [Aave V2](https://app.aave.com/#/dashboard).

```taster
Q.aaveV2.setUseReserveAsCollateral("eth", true);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
