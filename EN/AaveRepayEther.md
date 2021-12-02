```meta-Currency
```

# Repay ETH in Aave V2

In this scenario, you will repay ETH in Aave V2.

### Confirm your asset for repayment

- Choose type of asset to repay. Confirm value of asset to repay.
- Find out more about stable and variable interest rates [here](https://docs.aave.com/faq/borrowing#what-is-the-difference-between-stable-and-variable-rate).

- 1: stable
- 2: variable

```input-Dynamic
// Repay interest mode
let interestRateMode = 1;
```

```input-Verify
assert(interestRateMode == 1 || interestRateMode == 2, "Incorrect interest calculation.");
```

```output-Dynamic
let amountRepayMax = Q.aaveV2.getAmountRepayMax("ether", interestRateMode);
assert(amountRepayMax > 0.000001 ether, "Insufficient asset available for repay.");
print("Balance available to repay: " + amountRepayMax.toString());
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
assert(getBalance() >= amount, "Insufficient ETH available to repay.");
assert(amountRepayMax >= amount, "You cannot repay more than your loan.");
```

### Proceed Repay

- Now, Proceed repay.

```taster
Q.aaveV2.repay("ether", amount, interestRateMode);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
