```meta-Currency
```

# Deposit ETH in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will deposit ETH in BiFi.

### Deposit amount

- Type the amount of asset to deposit. (Error occured in case of insufficient ETH or invalid inputs.)

```input ETH
// Number of ETH to deposit
let amountDeposit = 0.1;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value");
assert(getBalance() >= amountDeposit, "Insufficient number of ETH");
```

### Proceed deposit

- Now, proceed loaning in BiFi.

```taster
Q.bifi.deposit("ether", amountDeposit);
```

### All steps are done successfully.

- You have successfully deposited ETH in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
