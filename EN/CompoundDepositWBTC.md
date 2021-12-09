```meta-Currency
wbtc
```

# Deposit WBTC in Compound

In this scenario, you will deposit WBTC in Compound.

### Deposit amount

- Type the amount of asset to deposit.

```input WBTC
// Amount of WBTC to deposit
let amountIn = 0.01;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(Q.erc20.balanceOf("wbtc") >= amountIn, "Insufficient WBTC");
```

### Proceed deposit

- Now, deposit your asset.

```taster
Q.compound.deposit("wbtc", amountIn);
```

### All steps are done successfully.

- Check your WBTC balance in [Compound](https://app.compound.finance/) and your connected wallet.
