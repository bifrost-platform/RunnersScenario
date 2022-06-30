```meta-Currency
```

# Repay BNB in Venus

In this scenario, you will repay BNB in Venus.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.venus.getRepayableAmount("bnb");
assert(amountRepayMax > 0.000001 bnb, "Insufficient asset available for repay.");
print("Balance available to repay: " + amountRepayMax.toString());
```

### Proceed Repay

- Type in asset to repay.

```input BNB
// Amount of BNB to repay
let amountRepay = 1.0;
```

```input-Verify
assert(amountRepay > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountRepay), "Invalid value.");
assert(getBalance() >= amountRepay, "Insufficient BNB to repay.");
assert(amountRepayMax >= amountRepay, "You cannot repay more than your loan.");
```

### Proceed Repay

- Now, Proceed repay.

```taster
Q.venus.repay("bnb", amountRepay);
```

### All steps are done successfully.

- Check your BNB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
