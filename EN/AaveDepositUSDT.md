```meta-Currency
usdt
```

# Deposit USDT in Aave V2

In this scenario, you will deposit USDT in Aave V2. This service may be limited according to the status of Aave V2.

### Deposit amount

- Type the amount of asset to deposit.

```input USDT
// Amount of USDT to deposit
let amountIn = 100;
```

```input-Verify
assert(Q.aaveV2.getIsActive("usdt") && !Q.aaveV2.getIsFrozen("usdt"), "Deposit is limited due to the circuit status of the market.");
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(Q.erc20.balanceOf("usdt") >= amountIn, "Insufficient USDT");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.aaveV2.deposit("usdt", amountIn);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
