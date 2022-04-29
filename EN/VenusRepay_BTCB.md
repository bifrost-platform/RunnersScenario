```meta-Currency
btcb
```

# Repay BTCB in Venus

In this scenario, you will repay BTCB in Venus.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.venus.getAmountRepayMax("btcb");
assert(amountRepayMax > 0.000001 btcb, "Insufficient asset available for repay.");
print("Balance available to repay: " + amountRepayMax.toString());
```

### Proceed Repay

- Type in asset to repay.

```input BTCB
// Amount of BTCB to repay
let amountRepay = 0.01;
```

```input-Verify
assert(amountRepay > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountRepay), "Invalid value.");
assert(Q.Token.balanceOf("btcb") >= amountRepay, "Insufficient BTCB to repay.");
assert(Q.venus.getAmountRepayMax("btcb") >= amountRepay, "You cannot repay more than your loan.");
```

### Proceed Repay

- Now, Proceed repay.

```taster
Q.venus.repay("btcb", amountRepay);
```

### All steps are done successfully.

- Check your BTCB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
