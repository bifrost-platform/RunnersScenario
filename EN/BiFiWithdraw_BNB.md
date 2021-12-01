```meta-Currency
```

# Withdraw BNB from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will withdraw BNB in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getMaxWithdrawAmount("bnb");
assert(amountWithdrawMax > 0.000001 bnb, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input bnb
// Amount of BNB to withdraw
let amountWithdraw = 0.1;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getMaxWithdrawAmount("bnb") >= amountWithdraw, "Insufficient BNB to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("bnb", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn BNB in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
