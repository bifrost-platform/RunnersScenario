```meta-Currency
usdt, 0x16b9a82891338f9bA80E2D6970FddA79D1eb0daE
```

# PancakeSwap에서 BNB-USDT 유동성 공급하기

Chainrunner Q는 이 문서의 내용대로, PancakeSwap에 BNB-USDT 풀에 유동성을 공급합니다.
BNB의 절반을 USDT로 바꾸어 동일 금액의 BNB-USDT 쌍을 PancakeSwap에 공급합니다.

### 사용할 BNB를 입력받습니다.

- 유동성 풀에 공급할 BNB를 입력합니다. 입력받은 BNB의 절반은 USDT로 교환됩니다.

```input BNB
// BNB 수량을 결정해주세요.
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountIn <= getBalance(), "BNB 잔액이 부족합니다." );
```

### 공급할 USDT를 구매합니다.

- 입력된 BNB의 절반을 USDT로 교환합니다.
- PancakeSwap 기본 슬리피지 값(0.5%)을 적용합니다.

```taster
let amountUsdt = Q.pancake.swapExactBNBForTokens ("usdt", amountIn / 2);
```

### 유동성을 공급합니다.

- 교환된 USDT와 남은 BNB를 PancakeSwap의 풀에 공급합니다.

```taster
Q.pancake.addLiquidityBNB ("usdt", amountIn / 2, amountUsdt);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 유동성 공급이 완료되었습니다.
- [PancakeSwap](https://pancakeswap.finance/liquidity)에서 유동성 공급 현황을 확인할 수 있습니다.
