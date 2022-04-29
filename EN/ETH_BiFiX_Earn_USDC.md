```meta-Currency
bifi, usdc
```

# Earn USDC in BiFi-X

Start yield farming(Earn) after leveraging at maximum boost in BiFi-X.

### Set amount of USDC to use.

- Please check your deposit of USDC and enter the amount to use.
- If you do not have any deposit of USDC, use the **Buy Tokens** menu.

```input USDC
let amount = 1000;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= Q.Token.balanceOf ("usdc"), "Insufficient USDC." );
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

### Leverage USDC to BiFi-X at the maximum boost and Earn.

```taster
// Confirm the maximum boost of USDC to leverage in BiFi-X.
let maxBoost = Q.bifiX.getMaxBoost ("usdc");

// Approve USDC before starting position.
Q.bifiX.approve("usdc", amount);

// Start Earn postion
Q.bifiX.earn("usdc", amount, maxBoost);
```

### All steps are done successfully.

- Check your positions in [BiFi-X](https://x.bifi.finance/).
