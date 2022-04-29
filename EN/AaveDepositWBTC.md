```meta-Currency
wbtc
```

# Deposit WBTC in Aave V2

In this scenario, you will deposit WBTC in Aave V2. This service may be limited according to the status of Aave V2.

### Deposit amount

- Type the amount of asset to deposit.

```input WBTC
// Deposit amount of WBTC
let amountIn = 0.01;
```

```input-Verify
assert(Q.aaveV2.getIsActive("wbtc") && !Q.aaveV2.getIsFrozen("wbtc"), "Deposit is limited due to the circuit status of the market.");
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(Q.Token.balanceOf("wbtc") >= amountIn, "Insufficient WBTC");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.aaveV2.deposit("wbtc", amountIn);
```

### Set your deposit as collateral

- This step enables your deposit to be set as a collateral.

- You can borrow assets from Aave V2 if you set your deposit as collateral.
- This step is optional. You may change collateral activation settings in [Aave V2](https://app.aave.com/#/dashboard).

```taster
Q.aaveV2.setUseReserveAsCollateral("wbtc", true);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
