```meta-Currency
ousdc
```

# Borrow oUSDC from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will borrow oUSDC from BiFi.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.bifi.getBorrowableAmount("ousdc");
assert(amountBorrowMax > 0.000001 ousdc, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input oUSDC
// Amount of oUSDC to borrow (Decimals allowed.)
let amountBorrow = 100;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value");
assert(Q.bifi.getBorrowableAmount("ousdc") >= amountBorrow, "Insufficient oUSDC to borrow.");
```

### Proceed loaning

- Now, proceed loaning in BiFi.

```taster
Q.bifi.borrow("ousdc", amountBorrow);
```

### All steps are done successfully.

- You have successfully borrowed oUSDC in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
