```meta-Currency
kwbtc
```

# Withdraw KWBTC from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will withdraw KWBTC in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getMaxWithdrawAmount("kwbtc");
assert(amountWithdrawMax > 0.000001 kwbtc, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input KWBTC
// Amount of KWBTC to withdraw
let amountWithdraw = 0.01;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getMaxWithdrawAmount("kwbtc") >= amountWithdraw, "Insufficient KWBTC to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("kwbtc", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn KWBTC in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
