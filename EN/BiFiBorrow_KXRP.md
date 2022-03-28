```meta-Currency
kxrp
```

# Borrow KXRP from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will borrow KXRP from BiFi.

### Confirm loanable amount.

- Confirm amount of asset available to borrow.

```output-Dynamic
let amountBorrowMax = Q.bifi.getMaxBorrowAmount("kxrp");
assert(amountBorrowMax > 0.000001 kxrp, "Insufficient asset to borrow.");
print("Loanable amount: " + amountBorrowMax.toString());
```

### Set amount of asset to borrow.

- Type in the amount of asset to borrow.

```input KXRP
// Amount of KXRP to borrow (Decimals allowed.)
let amountBorrow = 100;
```

```input-Verify
assert(amountBorrow > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountBorrow), "Invalid value");
assert(Q.bifi.getMaxBorrowAmount("kxrp") >= amountBorrow, "Insufficient KXRP to borrow.");
```

### Proceed loaning

- Now, proceed loaning in BiFi.

```taster
Q.bifi.borrow("kxrp", amountBorrow);
```

### All steps are done successfully.

- You have successfully borrowed KXRP in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
