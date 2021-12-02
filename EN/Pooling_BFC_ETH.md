```meta-Currency
bfc, 0x281df7fc89294c84afa2a21ffee8f6807f9c9226
```

# Deposit LP tokens inside BiFi Pooling

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will use BiFi pooling service.

FIrst, provide liquidity of BFC-WETH pool (5:5) of SushiSwap V2, and deposit the according LP tokens inside BiFi.

### Set amount of ETH to use.

- In this step, you will swap half of your ETH to BFC and provide liquidity inside BFC-WETH pool of SushiSwap V2. WETH(Wrapped WTH) is ERC20 token made to swap ETH and ERC20 tokens. Sushiswap provides BFC-WETH pool to provide liquidity of BFC-ETH pair.

```input ETH
// Total ETH.
let amount = 0.1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= getBalance (), "Insufficient ETH." );
```

### Swap ETH to BFC in SushiSwap.

- In this step, you will swap ETH to BFC to provide liquidity inside SushiSwap. Use default Sushiswap slippage (0.5%)

```taster
// Swap half of your ETH to BFC
let bfcAmount = Q.sushi.swapExactETHForTokens ("bfc", amount / 2);
assert (bfcAmount > 0, "BFC balance: 0");
```

### Provide liquidity of BFC-WETH pair in SushiSwap.

- Use default Sushiswap slippage (0.5%)

```taster
let lpAmount = Q.sushi.addLiquidityETH ("bfc", bfcAmount, amount / 2);
assert (lpAmount > 0, "Liquidity token balance: 0");
```

### Now, let's pool your LP tokens inside BiFi. You will be rewarded with BiFi tokens when you provide liquidity inside BiFi with LP tokens of SushiSwap.

```taster
// Now, let's pool your LP tokens inside BiFi.
Q.bifi.depositLp ("bfc", lpAmount);
```

### All steps are done successfully.

- Check your pooling status in [BiFi](https://app.bifi.finance/pool/sushiswap/bfcEth?chainid=mainnet).
