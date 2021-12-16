```meta-Currency
bifi, 0x0beC54c89a7d9F15C4e7fAA8d47ADEdF374462eD
```

# Deposit LP tokens of BiFi-WETH pair inside BiFi Pooling

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will use BiFi pooling service.

FIrst, provide liquidity of BiFi-WETH pool (5:5) of SushiSwap V2, and deposit the according LP tokens inside BiFi.

### Set amount of BiFi to use.

- In this step, you will provide liquidity of BiFi-WETH pair in Sushiswap V2 and deposit the according LP tokens inside BiFi staking pool.
- WETH(Wrapped WTH) is ERC20 token made to swap ETH and ERC20 tokens. Sushiswap provides BiFi-WETH pool to provide liquidity of BiFi-ETH pair.
- Please check your deposit of BiFi and enter the amount to use.
- If you do not have any deposit of BiFi, use the **Buy Tokens** menu.

```input BiFi
// Total BiFi.
let bifiAmount = 1000;
```

```input-Verify
proc getETHAmountsOutFromExactIn (tokenName, amountIn) {
  let tokenAddr = erc20.getTokenAddr (tokenName);
  let path = [tokenAddr, sushiswapV2.router02.getWethAddress()];
  let results = sushiswapV2.router02.getAmountsOut (amountIn, path);
  return numToCurrency (results[1], "eth", 18);
}

assert(bifiAmount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (bifiAmount), "Invalid value");
assert(bifiAmount <= Q.erc20.balanceOf ("bifi"), "Insufficient BIFI." );
let ethBalance = getBalance ();
let ethAmount = getETHAmountsOutFromExactIn("bifi", bifiAmount);
assert(ethAmount <= ethBalance, "Insufficent ETH. Please set lower amount of BiFi." );
```

### Provide liquidity of BiFi-WETH pair in SushiSwap.

- Use default Sushiswap slippage (0.5%)

```taster
let lpAmount = Q.sushi.addLiquidityETH ("bifi", bifiAmount, ethAmount);
assert (lpAmount > 0, "Liquidity token balance: 0");
```

### Now, let's pool your LP tokens inside BiFi. You will be rewarded with BiFi tokens when you provide liquidity inside BiFi with LP tokens of SushiSwap.

```taster
// Now, let's pool your LP tokens inside BiFi.
Q.bifi.depositLp ("bifi", lpAmount);
```

### All steps are done successfully.

- Check your pooling status in [BiFi](https://app.bifi.finance/pool/sushiswap/bifiEth?chainid=mainnet).
