```meta-Currency
wbtc
```

# Deposit WBTC in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will deposit WBTC in BiFi.

### Deposit amount

- Type the amount of asset to deposit. (Error occured in case of insufficient WBTC or invalid inputs.)

```input WBTC
// Deposit amount of WBTC
let amountDeposit = 0.01;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value");
assert(Q.erc20.balanceOf("wbtc") >= amountDeposit, "Insufficient WBTC");
```

### Deposit in BiFi

- Now, proceed loaning in BiFi.

```taster
Q.bifi.deposit("wbtc", amountDeposit);
```

### All steps are done successfully.

- You have successfully deposited WBTC in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
