```meta-Currency
bifi, usdt
```

# Earn USDT in BiFi-X

Start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of USDT to use.

- Please check your deposit of USDT and enter the amount to use.
- If you do not have any deposit of USDT, use the **Buy Tokens** menu.

```input USDT
let amount = 100;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= Q.erc20.balanceOf ("usdt"), "Insufficient USDT." );
```

### Swap ETH to BiFi in Sushiswap.

- Use default Sushiswap slippage (0.5%)
- This step will not be processed if you're already holding enough balance of BiFi tokens

```taster
let bifiBalance = Q.erc20.balanceOf ("bifi");
let bifiFee = Q.bifiX.getFee ();
if (bifiBalance < bifiFee) {
    Q.sushi.swapETHForExactTokens ("bifi", bifiFee - bifiBalance);
}
```

### Confirm BiFi to be used for service fee in BiFi-X.

```taster
Q.bifiX.approve("bifi", bifiFee);
```

### Leverage USDT to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of USDT to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("usdt");

// Approve USDT before starting position.
Q.bifiX.approve("usdt", amount);

// Start Earn postion
Q.bifiX.createEarnPosition ("usdt", amount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/).
