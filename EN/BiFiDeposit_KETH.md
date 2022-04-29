```meta-Currency
keth
```

# Deposit KETH in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will deposit KETH in BiFi.

### Deposit amount

- Type the amount of asset to deposit. (Error occured in case of insufficient KETH or invalid inputs.)

```input KETH
// Amount of KETH to deposit
let amountDeposit = 0.1;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value");
assert(Q.Token.balanceOf("keth") >= amountDeposit, "Insufficient KETH");
```

### Deposit in BiFi

- Now, proceed loaning in BiFi.

```taster
Q.bifi.deposit("keth", amountDeposit);
```

### All steps are done successfully.

- You have successfully deposited KETH in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
