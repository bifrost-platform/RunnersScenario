```meta-Currency
oeth
```

# Withdraw oETH from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will withdraw oETH in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getWithdrawableAmount("oeth");
assert(amountWithdrawMax > 0.000001 oeth, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input oETH
// Amount of oETH to withdraw (Decimals allowed.)
let amountWithdraw = 100;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getWithdrawableAmount("oeth") >= amountWithdraw, "Insufficient oETH to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("oeth", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn oETH in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
