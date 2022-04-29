```meta-Currency
btcb
```

# Deposit BTCB in BiFi

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will deposit BTCB(Binance-Peg BTCB) in BiFi.

### Deposit amount

- Type the amount of asset to deposit. (Error occured in case of insufficient BTCB or invalid inputs.)

```input BTCB
// BTCB to deposit
let amountDeposit = 0.01;
```

```input-Verify
assert(amountDeposit > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountDeposit), "Invalid value");
assert(Q.Token.balanceOf("btcb") >= amountDeposit, "Insufficient BTCB");
```

### Deposit in BiFi

- Now, proceed deposit in BiFi.

```taster
Q.bifi.deposit("btcb", amountDeposit);
```

### All steps are done successfully.

- You have successfully deposited BTCB in BiFi.
- Check your balance in [BiFi App](https://app.bifi.finance/).
