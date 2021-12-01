```meta-Currency
usdt
```

# Borrow USDT from Aave V2

In this scenario, you will borrow USDT in Aave V2.

### Confirm loanable amount.

- Value shown may not be accurate. or precise value, please obtain asset directly from [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
let amountBorrowMax = Q.aaveV2.getAmountBorrowMax("usdt");
assert(amountBorrowMax > 0.000001 usdt, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input USDT
// Amount of USDT to borrow
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amount), "Invalid value");
assert(amountBorrowMax >= amount, "Insufficient USDT to borrow.");
```

### Setting interest rates

- When loaning in Aave V2, you must choose between stable and variable rates. Find out more about stable and variable interest rates [here](https://docs.aave.com/faq/borrowing#what-is-the-difference-between-stable-and-variable-rate).

- 1: stable
- 2: variable

```input
// Interest rate modes
let interestRateMode = 1;
```

```input-Verify
assert(interestRateMode == 1 || interestRateMode == 2, "Incorrect interest calculation.");
```

### Proceed loaning

- Now, borrow asset.

```taster
Q.aaveV2.borrow("usdt", amount, interestRateMode);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
