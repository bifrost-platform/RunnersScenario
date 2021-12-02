```meta-Currency
bifi, 0x0beC54c89a7d9F15C4e7fAA8d47ADEdF374462eD
```

# Deposit LP tokens of BiFi-WETH pair inside BiFi Pooling

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will use BiFi pooling service.

FIrst, provide liquidity of BiFi-WETH pool (5:5) of SushiSwap V2, and deposit the according LP tokens inside BiFi.

### Set amount of ETH to use.

- In this step, you will swap half of your ETH to BiFi and provide liquidity inside BiFi-WETH pool of SushiSwap V2. WETH(Wrapped WTH) is ERC20 token made to swap ETH and ERC20 tokens. Sushiswap provides BiFi-WETH pool to provide liquidity of BiFi-ETH pair.

```input ETH
// Total ETH.
let amount = 0.1;
```

```input-Verify
assert(amount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (amount), "Invalid value");
assert(amount <= getBalance (), "Insufficient ETH." );
```

### Swap ETH to BiFi in SushiSwap.

- In this step, you will swap ETH to BiFi to provide liquidity inside SushiSwap. Use default Sushiswap slippage (0.5%)

```taster
// Swap half of your ETH to BiFi
let bifiAmount = Q.sushi.swapExactETHForTokens ("bifi", amount / 2);
assert (bifiAmount > 0, "BiFi balance: 0");
```

### Provide liquidity of BiFi-WETH pair in SushiSwap.

- Use default Sushiswap slippage (0.5%)

```taster
let lpAmount = Q.sushi.addLiquidityETH ("bifi", bifiAmount, amount / 2);
assert (lpAmount > 0, "Liquidity token balance: 0");
```

### Now, let's pool your LP tokens inside BiFi. You will be rewarded with BiFi tokens when you provide liquidity inside BiFi with LP tokens of SushiSwap.

```taster
// Now, let's pool your LP tokens inside BiFi.
Q.bifi.depositLp ("bifi", lpAmount);
```

### All steps are done successfully.

- Check your pooling status in [BiFi](https://app.bifi.finance/pool/sushiswap/bifiEth?chainid=mainnet).
