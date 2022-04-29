```meta-Currency
kxrp
```

# Repay KXRP in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will repay KXRP in BiFi.

### Confirm your asset for repayment

- Confirm your asset available to repay.

```output-Dynamic
let amountRepayMax = Q.bifi.getMaxRepayAmount("kxrp");
assert(amountRepayMax > 0.000001 kxrp, "Insufficient asset available for repay.");
print("Balance available to repay: " + amountRepayMax.toString());
```

### Proceed Repay

- Type in asset to repay.

```input KXRP
// Amount of KXRP to repay (Decimals allowed.)
let amountRepay = 100;
```

```input-Verify
assert(amountRepay > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountRepay), "Invalid value");
assert(Q.Token.balanceOf("kxrp") >= amountRepay, "Insufficient KXRP available to repay.");
assert(Q.bifi.getMaxRepayAmount("kxrp") >= amountRepay, "You cannot repay more than your loan.");
```

### Proceed Repay

- Now, proceed repay in BiFi.

```taster
Q.bifi.repay("kxrp", amountRepay);
```

### All steps are done successfully.

- You have successfully repaid KXRP in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
