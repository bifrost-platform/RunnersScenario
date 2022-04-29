```meta-Currency
usdt
```

# Repay USDT in Aave V2

In this scenario, you will repay USDT in Aave V2. This service may be limited according to the status of Aave V2.

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
assert(Q.aaveV2.getIsActive("usdt"), "Repayment is limited due to the circuit status of the market.");
let amountRepayMax = Q.aaveV2.getAmountRepayMax("usdt", interestRateMode);
assert(amountRepayMax > 0.000001 usdt, "Insufficient asset available for repay.");
print("Balance available to repay: " + amountRepayMax.toString());
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
assert(Q.Token.balanceOf("usdt") >= amount, "Insufficient USDT available to repay.");
assert(amountRepayMax >= amount, "You cannot repay more than your loan.");
```

### Proceed Repay

- Now, Proceed repay.

```taster
Q.aaveV2.repay("usdt", amount, interestRateMode);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
