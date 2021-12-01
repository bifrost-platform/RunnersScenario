```meta-Currency
```

# Borrow BNB from Venus

In this scenario, you will borrow BNB in Venus.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.venus.getAmountBorrowMax("bnb");
assert(amountBorrowMax > 0.000001 bnb, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input BNB
// Amount of BNB to borrow
let amountBorrow = 1.0;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value.");
assert(amountBorrowMax >= amountBorrow, "Insufficient BNB to borrow.");
```

### Proceed loaning

- Now, borrow asset.
- Some services may not indicate success or failure if it exceeds the loanable amount. Please check [Venus](https://app.venus.io/dashboard) for the exact status.
- Please check the status of your loan in [Venus](https://app.venus.io/dashboard).

```taster
Q.venus.borrow("bnb", amountBorrow);
```

### All steps are done successfully.

- Check your BNB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
