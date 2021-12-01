```meta-Currency
usdt
```

# Repay USDT in Compound

In this scenario, you will repay USDT in Compound.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.compound.getRepayAmount ("usdt");
assert (amountRepayMax >= 0.000001 usdt, "Insufficient asset available for repay.");
print ("Balance available to repay: " + amountRepayMax.toString ());
```

### Proceed Repay

- Type in asset to repay.

```input USDT
// Amount of USDT to repay
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amount), "Invalid value");
assert(Q.erc20.balanceOf("usdt") >= amount, "Insufficient USDT to repay.");
assert(amountRepayMax >= amount, "You cannot repay more than your loan.");
```

### Proceed repay

- Now, Proceed repay.

```taster
Q.compound.repay("usdt", amount);
```

### All steps are done successfully.

- Check your USDT balance in [Compound](https://app.compound.finance/) and your connected wallet.
