```meta-Currency
usdt
```

# Borrow USDT from Venus

In this scenario, you will borrow USDT in Venus.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.venus.getAmountBorrowMax("usdt");
assert(amountBorrowMax > 0.000001 usdt, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input USDT
// Amount of USDT to borrow
let amountBorrow = 100;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value.");
assert(Q.venus.getAmountBorrowMax("usdt") >= amountBorrow, "Insufficient USDT to borrow.");
```

### Proceed loaning

- Now, borrow asset.
- Some services may not indicate success or failure if it exceeds the loanable amount. Please check [Venus](https://app.venus.io/dashboard) for the exact status.
- Please check the status of your loan in [Venus](https://app.venus.io/dashboard).

```taster
Q.venus.borrow("usdt", amountBorrow);
```

### All steps are done successfully.

- Check your USDT balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
