```meta-Currency
usdt, 0x16b9a82891338f9bA80E2D6970FddA79D1eb0daE
```

# Provide liquidity of BNB-USDT in PancakeSwap

In this scenario, you will provide liquidity of BNB-USDT pool. You will start with swapping half of your BNB tokens to USDT, and providing the other half together inside the liquidity pool of PancakeSwap.

### Set amount of BNB to use.

- Set the total amount of BNB to use for the liqidity pool. Half of your BNB tokens will be swapped with USDT for BNB-USDT pair.

```input BNB
// Total BNB.
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "Incorrect value. Please enter value more than 0.");
assert(isCurrency(amountIn), "Invalid value");
assert(amountIn <= getBalance(), "Insufficient BNB." );
```

### Buy USDT

- Swap half of your BNB tokens to USDT.
- Default PancakeSwap slippage (0.5%)

```taster
let amountUsdt = Q.pancake.getAmountOut ("bnb", "usdt", amountIn / 2);
Q.pancake.sell ("bnb", "usdt", amountIn / 2);
```

### Provide liquidity.

- Provide liquidity in PancakeSwap with your swapped USDT and BNB.

```taster
Q.pancake.addLiquidityBNB ("usdt", amountIn / 2, amountUsdt);
```

### All steps are done successfully.

- Now check your liquidity in [PancakeSwap](https://pancakeswap.finance/liquidity).
