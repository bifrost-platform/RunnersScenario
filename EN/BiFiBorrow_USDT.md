```meta-Currency
usdt
```

# Borrow USDT from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will borrow USDT from BiFi.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.bifi.getMaxBorrowAmount("usdt");
assert(amountBorrowMax > 0.000001 usdt, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input USDT
// Amount of USDT to borrow (Decimals allowed.)
let amountBorrow = 100;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value");
assert(Q.bifi.getMaxBorrowAmount("usdt") >= amountBorrow, "Insufficient USDT to borrow.");
```

### Proceed loaning

- Now, proceed loaning in BiFi.

```taster
Q.bifi.borrow("usdt", amountBorrow);
```

### All steps are done successfully.

- You have successfully borrowed USDT in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
