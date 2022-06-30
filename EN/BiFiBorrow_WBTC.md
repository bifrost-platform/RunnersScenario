```meta-Currency
wbtc
```

# Borrow WBTC from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will borrow WBTC from BiFi.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.bifi.getBorrowableAmount("wbtc");
assert(amountBorrowMax > 0.000001 wbtc, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input WBTC
// Amount of WBTC to borrow
let amountBorrow = 0.01;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value");
assert(Q.bifi.getBorrowableAmount("wbtc") >= amountBorrow, "Insufficient WBTC to borrow.");
```

### Proceed loaning

- Now, proceed loaning in BiFi.

```taster
Q.bifi.borrow("wbtc", amountBorrow);
```

### All steps are done successfully.

- You have successfully borrowed WBTC in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
