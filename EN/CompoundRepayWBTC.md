```meta-Currency
wbtc
```

# Repay WBTC in Compound

In this scenario, you will repay WBTC in Compound.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.compound.getRepayAmount ("wbtc");
assert (amountRepayMax >= 0.000001 wbtc, "Insufficient asset available for repay.");
print ("Balance available to repay: " + amountRepayMax.toString ());
```

### Proceed Repay

- Type in asset to repay.

```input WBTC
// Amount of WBTC to repay
let amount = 0.01;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amount), "Invalid value");
assert(Q.Token.balanceOf("wbtc") >= amount, "Insufficient WBTC to repay.");
assert(amountRepayMax >= amount, "You cannot repay more than your loan.");
```

### Proceed repay

- Now, Proceed repay.

```taster
Q.compound.repay("wbtc", amount);
```

### All steps are done successfully.

- Check your WBTC balance in [Compound](https://app.compound.finance/) and your connected wallet.
