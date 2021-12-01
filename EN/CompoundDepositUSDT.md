```meta-Currency
usdt
```

# Deposit USDT in Compound

In this scenario, you will deposit USDT in Compound.

### Deposit amount

- Type the amount of asset to deposit.

```input USDT
// Amount of USDT to deposit
let amountIn = 100;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(Q.erc20.balanceOf("usdt") >= amountIn, "Insufficient USDT");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.compound.deposit ("usdt", amountIn);
```

### All steps are done successfully.

- Check your USDT balance in [Compound](https://app.compound.finance/) and your connected wallet.
