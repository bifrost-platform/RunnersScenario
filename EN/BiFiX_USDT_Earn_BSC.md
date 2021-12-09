```meta-Currency
bifi, usdt
```

# Earn USDT in BiFi-X

In this scenario, you will start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Confirm BiFi to be used for service fee in BiFi-X.

- To use BiFi-X service, you need to hold BiFi tokens in your wallet to pay for service fee.

```output-Dynamic
let bifiFee = Q.bifiX.getFee ();
let bifiBalance = Q.erc20.balanceOf ("bifi");
assert(bifiBalance >= bifiFee, "Insufficient BiFi.");
print ("BiFi tokens needed for service fee: " + bifiFee.toString ());
```

### Set amount of USDT to use.

- Please check your deposit of USDT and enter the amount to use.
- If you do not have any deposit of USDT, use the **Buy Tokens** menu.

```input USDT
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= Q.erc20.balanceOf ("usdt"), "Insufficient USDT." );
```

### Confirm BiFi to be used for service fee in BiFi-X.

```taster
Q.bifiX.approveBiFi (bifiFee);
```

### Leverage USDT to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of USDT to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("usdt");

// Approve USDT before starting position.
let usdtTokenAddr = erc20.getTokenAddr ("usdt");
let xFactoryAddr = bifiX.xFactory.getAddress ();
erc20.approve (usdtTokenAddr, xFactoryAddr, amount);

// Start Earn position
Q.bifiX.createEarnPosition ("usdt", amount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
