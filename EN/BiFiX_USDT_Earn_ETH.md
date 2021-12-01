```meta-Currency
bifi, usdt
```

# Earn USDT in BiFi-X

Swap ETH to USDT, and start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of ETH to use.

```input ETH
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= getBalance (), "Insufficient ETH." );
```

### Swap ETH to USDT in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
let usdtAmount = Q.sushi.swapExactETHForTokens ("usdt", amount);
```

### Swap ETH to BiFi in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
let bifiFee = Q.bifiX.getFee ();
Q.sushi.swapETHForExactTokens ("bifi", bifiFee);
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
erc20.approve (usdtTokenAddr, xFactoryAddr, usdtAmount);

// Start Earn postion
Q.bifiX.createEarnPosition ("usdt", usdtAmount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/).
