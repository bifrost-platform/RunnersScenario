```meta-Currency
wbtc
```

# Borrow WBTC from Compound

In this scenario, you will borrow WBTC in Compound.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.
- Value shown may not be accurate. or precise value, please obtain asset directly from [Compound](https://app.compound.finance/).

```output-Dynamic
let amountBorrowMax = Q.compound.getBorrowableAmount("wbtc");
assert(amountBorrowMax >= 0.000001 wbtc, "Insufficient WBTC available to borrow in Compound.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input WBTC
// Amount of WBTC to borrow
let amount = 0.01;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amount), "Invalid value");
assert(amountBorrowMax >= amount, "Insufficient WBTC available to borrow.");
```

### Proceed lending

- Now, borrow asset.
- Some services may not indicate success or failure if it exceeds the loanable amount. Please check [Compound](https://app.compound.finance/) for the exact status.
- Please check the status of your loan in [Compound](https://app.compound.finance/).

```taster
Q.compound.borrow("wbtc", amount);
```

### All steps are done successfully.

- Check your WBTC balance in [Compound](https://app.compound.finance/) and your connected wallet.
