```meta-Currency
usdt
```

# Repay USDT in Venus

In this scenario, you will repay USDT in Venus.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.venus.getAmountRepayMax("usdt");
assert(amountRepayMax > 0.000001 usdt, "Insufficient asset available for repay.");
print("Balance available to repay: " + amountRepayMax.toString());
```

### Proceed Repay

- Type in asset to repay.

```input USDT
// Amount of USDT to repay
let amountRepay = 100;
```

```input-Verify
assert(amountRepay > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountRepay), "Invalid value.");
assert(Q.Token.balanceOf("usdt") >= amountRepay, "Insufficient USDT to repay.");
assert(Q.venus.getAmountRepayMax("usdt") >= amountRepay, "You cannot repay more than your loan.");
```

### Proceed Repay

- Now, Proceed repay.

```taster
Q.venus.repay("usdt", amountRepay);
```

### All steps are done successfully.

- Check your USDT balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
