```meta-Currency
bifi, link
```

# Earn LINK in BiFi-X

Swap ETH to LINK, and start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of ETH to use.

```input ETH
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= getBalance (), "Insufficient ETH." );
```

### Swap ETH to LINK in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
let linkAmount = Q.sushi.swapExactETHForTokens ("link", amount);
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
Q.bifiX.approveBiFi (bifiFee);
```

### Leverage LINK to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of LINK to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("link");

// Approve LINK before starting position.
let linkTokenAddr = erc20.getTokenAddr ("link");
let xFactoryAddr = bifiX.xFactory.getAddress ();
erc20.approve (linkTokenAddr, xFactoryAddr, linkAmount);

// Start Earn postion
Q.bifiX.createEarnPosition ("link", linkAmount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/).
