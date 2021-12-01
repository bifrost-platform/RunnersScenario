```meta-Currency
bifi, btcb
```

# Earn BTCB in BiFi-X

In this scenario, you will swap ETH to BTCB and start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Confirm BiFi to be used for service fee in BiFi-X.

- To use BiFi-X service, you need to hold BiFi tokens in your wallet to pay for service fee.

```output-Dynamic
let bifiFee = Q.bifiX.getFee ();
let bifiBalance = Q.erc20.balanceOf ("bifi");
assert(bifiBalance >= bifiFee, "Insufficient BiFi");
print ("BiFi tokens needed for service fee: " + bifiFee.toString ());
```

### Set amount of BNB to use.

```input BNB
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value.");
assert(isCurrency (amount), "Incorrect format.");
assert(amount <= getBalance (), "Insufficient BNB.");
```

### Swap BNB to BTCB in PancakeSwap.

- Use default PancakeSwap slippage (0.5%)

```taster
let btcbAmount = Q.pancake.swapExactBNBForTokens ("btcb", amount);
```

### Confirm BiFi to be used for service fee in BiFi-X.

```taster
Q.bifiX.approveBiFi (bifiFee);
```

### Leverage BTCB to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of BTCB to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("btcb");

// Approve BTCB before starting position.
let btcbTokenAddr = erc20.getTokenAddr ("btcb");
let xFactoryAddr = bifiX.xFactory.getAddress ();
erc20.approve (btcbTokenAddr, xFactoryAddr, btcbAmount);

// Start Earn position
Q.bifiX.createEarnPosition ("btcb", btcbAmount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/) now.
