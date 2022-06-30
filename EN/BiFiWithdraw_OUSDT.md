```meta-Currency
ousdt
```

# Withdraw oUSDT from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will withdraw oUSDT in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getWithdrawableAmount("ousdt");
assert(amountWithdrawMax > 0.000001 ousdt, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input oUSDT
// Amount of oUSDT to withdraw (Decimals allowed.)
let amountWithdraw = 100;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getWithdrawableAmount("ousdt") >= amountWithdraw, "Insufficient oUSDT to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("ousdt", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn oUSDT in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
