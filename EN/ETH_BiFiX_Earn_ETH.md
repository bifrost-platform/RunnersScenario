```meta-Currency
bifi
```

# Earn ETH in BiFi-X

Start yield farming(Earn) after leveraging ETH at maximum boost in BiFi-X.

### Set amount of ETH to use.

```input ETH
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= getBalance (), "Insufficient ETH." );
```

### Swap ETH to BiFi in Sushiswap.

- Use default Sushiswap slippage (0.5%)
- This step will not be processed if you're already holding enough balance of BiFi tokens

```taster
let bifiBalance = Q.Token.balanceOf ("bifi");
let bifiFee = Q.bifiX.getFee ();
if (bifiBalance < bifiFee) {
    Q.sushi.swapETHForExactTokens ("bifi", bifiFee - bifiBalance);
}
```

### Confirm BiFi to be used for service fee in BiFi-X.

```taster
Q.bifiX.approve("bifi", bifiFee);
```

### Leverage ETH to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of ETH to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("ether");

// Start Earn postion
Q.bifiX.earn("ether", amount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/).
