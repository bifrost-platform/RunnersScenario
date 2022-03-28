```meta-Currency
```

# Deposit KLAY in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will deposit KLAY in BiFi.

### Deposit amount

- Type the amount of asset to deposit. (Error occured in case of insufficient KLAY or invalid inputs.)

```input klay
// KLAY to deposit
let amountDeposit = 0.1;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value");
assert(getBalance() >= amountDeposit, "Insufficient KLAY");
```

### Proceed deposit

- Now, proceed loaning in BiFi.

```taster
Q.bifi.deposit("klay", amountDeposit);
```

### All steps are done successfully.

- You have successfully deposited KLAY in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
