```meta-Currency
bifi, dai
```

# Earn DAI in BiFi-X

Swap ETH to DAI, and start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of ETH to use.

```input ETH
let amount = 1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= getBalance (), "Insufficient ETH." );
```

### Swap ETH to DAI in Sushiswap.

- Use default Sushiswap slippage (0.5%)

```taster
let daiAmount = Q.sushi.swapExactETHForTokens ("dai", amount);
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

### Leverage DAI to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of DAI to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("dai");

// Approve DAI before starting position.
let daiTokenAddr = erc20.getTokenAddr ("dai");
let xFactoryAddr = bifiX.xFactory.getAddress ();
erc20.approve (daiTokenAddr, xFactoryAddr, daiAmount);

// Start Earn postion
Q.bifiX.createEarnPosition ("dai", daiAmount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/).
