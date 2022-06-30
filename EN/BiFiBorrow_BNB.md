```meta-Currency
```

# Borrow BNB from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will borrow BNB from BiFi.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.bifi.getBorrowableAmount("bnb");
assert(amountBorrowMax > 0.000001 bnb, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input bnb
// Amount of BNB to borrow
let amountBorrow = 0.1;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value");
assert(Q.bifi.getBorrowableAmount("bnb") >= amountBorrow, "Insufficient BNB to borrow.");
```

### Proceed loaning

- Now, proceed loaning in BiFi.

```taster
Q.bifi.borrow("bnb", amountBorrow);
```

### All steps are done successfully.

- You have successfully borrowed BNB in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
