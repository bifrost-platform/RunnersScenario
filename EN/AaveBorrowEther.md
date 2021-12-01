```meta-Currency
```

# Borrow Ether from Aave V2

In this scenario, you will borrow Ether in Aave V2.

### Confirm loanable amount.

- Value shown may not be accurate. or precise value, please obtain asset directly from [Aave V2](https://app.aave.com/#/dashboard).

```output-Dynamic
let amountBorrowMax = Q.aaveV2.getAmountBorrowMax("ether");
assert(amountBorrowMax > 0.000001 ether, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input ETH
// Number of ETH to loan
let amount = 0.1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amount), "Invalid value");
assert(amountBorrowMax >= amount, "Insufficient ETH to borrow.");
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
Q.aaveV2.borrow("ether", amount, interestRateMode);
```

### All steps are done successfully.

- Check your deposit in your connected wallet and [AAVE](https://app.aave.com/#/dashboard).
