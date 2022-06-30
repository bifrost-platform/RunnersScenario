```meta-Currency
ousdt
```

# Deposit oUSDT in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will deposit oUSDT in BiFi.

### Deposit amount

- Type the amount of asset to deposit. (Error occured in case of insufficient oUSDT or invalid inputs.)

```input oUSDT
// Amount of oUSDT to deposit (Decimals allowed.)
let amountDeposit = 100;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value");
assert(Q.Token.balanceOf("ousdt") >= amountDeposit, "Insufficient oUSDT");
```

### Deposit in BiFi

- Now, proceed loaning in BiFi.

```taster
Q.bifi.deposit("ousdt", amountDeposit);
```

### All steps are done successfully.

- You have successfully deposited oUSDT in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
