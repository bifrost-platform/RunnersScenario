```meta-Currency
```

# Repay ETH in Compound

In this scenario, you will repay ETH in Compound.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.compound.getRepayableAmount ("eth");
assert (amountRepayMax >= 0.000001 ether, "Insufficient asset available for repay.");
print ("Balance available to repay: " + amountRepayMax.toString ());
```

### Proceed Repay

- Type in asset to repay.

```input ETH
// Amount of ETH to repay
let amount = 0.1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amount), "Invalid value");
assert(getBalance() >= amount, "Insufficient ETH to repay.");
assert(amountRepayMax >= amount, "You cannot repay more than your loan.");
```

### Proceed repay

- Now, Proceed repay.

```taster
Q.compound.repay("eth", amount);
```

### All steps are done successfully.

- Check your ETH balance in [Compound](https://app.compound.finance/) and your connected wallet.
