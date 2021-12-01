```meta-Currency
btcb
```

# Borrow BTCB from Venus

In this scenario, you will borrow BTCB in Venus.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.venus.getAmountBorrowMax("btcb");
assert(amountBorrowMax > 0.000001 btcb, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input BTCB
// Amount of BTCB to borrow
let amountBorrow = 0.01;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value.");
assert(Q.venus.getAmountBorrowMax("btcb") >= amountBorrow, "Insufficient BTCB to borrow.");
```

### Proceed loaning

- Now, borrow asset.
- Some services may not indicate success or failure if it exceeds the loanable amount. Please check [Venus](https://app.venus.io/dashboard) for the exact status.
- Please check the status of your loan in [Venus](https://app.venus.io/dashboard).

```taster
Q.venus.borrow("btcb", amountBorrow);
```

### All steps are done successfully.

- Check your BTCB balance in your connected wallet and your [Venus](https://app.venus.io/dashboard) account.
