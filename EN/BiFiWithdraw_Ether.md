```meta-Currency
```

# Withdraw ETH from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will withdraw ETH in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getWithdrawableAmount("eth");
assert(amountWithdrawMax > 0.000001 ether, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input ETH
// Amount of ETH to withdraw
let amountWithdraw = 0.1;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getWithdrawableAmount("eth") >= amountWithdraw, "Insufficient ETH to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("eth", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn ETH in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
