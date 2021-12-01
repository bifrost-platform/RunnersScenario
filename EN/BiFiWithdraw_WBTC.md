```meta-Currency
wbtc
```

# Withdraw WBTC from BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will withdraw WBTC in BiFi.

### Confirm the amount available to withdraw

- Confirm asset available to withdraw.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getMaxWithdrawAmount("wbtc");
assert(amountWithdrawMax > 0.000001 wbtc, "Insufficient asset to withdraw.");
print("Asset available to withdraw: " + amountWithdrawMax.toString());
```

### Withdrawal amount

- Type in amount of asset to withdraw.

```input WBTC
// Amount of WBTC to withdraw
let amountWithdraw = 0.01;
```

```input-Verify
assert(amountWithdraw > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountWithdraw), "Invalid value");
assert(Q.bifi.getMaxWithdrawAmount("wbtc") >= amountWithdraw, "Insufficient WBTC to withdraw.");
```

### Proceed withdrawal

- Now, proceed withdrawal in BiFi.

```taster
Q.bifi.withdraw("wbtc", amountWithdraw);
```

### All steps are done successfully.

- You have successfully withdrawn USDT in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
