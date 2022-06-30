```meta-Currency
bfc, 0x281df7fc89294c84afa2a21ffee8f6807f9c9226
```

# Deposit LP tokens inside BiFi Pooling

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) supports lending services in various networks to ultimately function as a multichain DeFi.

In this scenario, you will use BiFi pooling service.

FIrst, provide liquidity of BFC-WETH pool (5:5) of SushiSwap V2, and deposit the according LP tokens inside BiFi.

### Set amount of BFC to use.

- In this step, you will provide liquidity of BFC-WETH pair in Sushiswap V2 and deposit the according LP tokens inside BiFi staking pool.
- WETH(Wrapped WTH) is ERC20 token made to swap ETH and ERC20 tokens. Sushiswap provides BFC-WETH pool to provide liquidity of BFC-ETH pair.
- Please check your deposit of BiFi and enter the amount to use.
- If you do not have any deposit of BiFi, use the **Buy Tokens** menu.

```input BFC
// Total BFC.
let bfcAmount = 1000;
```

```input-Verify
assert(bfcAmount > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency (bfcAmount), "Invalid value");
assert(bfcAmount <= Q.Token.balanceOf ("bfc"), "Insufficient BFC." );
let ethBalance = getBalance ();
let ethAmount = Q.sushi.getAmountIn ("eth", "bfc", bfcAmount);
assert(currencyToNum (ethAmount) <= currencyToNum (ethBalance), "Insufficent ETH. Please set lower amount of BFC." );
```

### Provide liquidity of BFC-WETH pair in SushiSwap.

- Use default Sushiswap slippage (0.5%)

```taster
let lpBalanceBefore = Q.sushi.getWETHLpBalance ("bfc");
Q.sushi.addLiquidityETH ("bfc", bfcAmount, ethAmount);
let lpBalanceAfter = Q.sushi.getWETHLpBalance ("bfc");
let lpAmount = lpBalanceAfter - lpBalanceBefore;
assert (lpAmount > 0, "Liquidity token balance: 0");
```

### Now, let's pool your LP tokens inside BiFi. You will be rewarded with BiFi tokens when you provide liquidity inside BiFi with LP tokens of SushiSwap.

```taster
// Now, let's pool your LP tokens inside BiFi.
Q.bifi.depositLp ("bfc", lpAmount);
```

### All steps are done successfully.

- Check your pooling status in [BiFi](https://app.bifi.finance/pool/sushiswap/bfcEth?chainid=mainnet).
