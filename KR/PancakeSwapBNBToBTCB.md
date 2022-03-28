```meta-Currency
btcb
```

# PancakeSwap에서 BNB를 BTCB로 교환하기

Chainrunner Q는 이 문서의 내용대로 PancakeSwap에서 BNB를 BTCB로 교환합니다.

### 교환할 BNB의 수량을 입력합니다.

```input-Dynamic BNB
let amountIn = 1.0;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountIn <= getBalance(), "BNB 잔액이 부족합니다.");
```

```output-Dynamic BTCB
let btcbAmount = Q.pancake.getAmountsOutFromExactIn("btcb", amountIn);
print(btcbAmount);
```

### PancakeSwap에서 BNB를 BTCB로 교환합니다.

- PancakeSwap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
// BNB를 BTCB로 교환합니다.
Q.pancake.swapExactBNBForTokens("btcb", amountIn);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 좌측 상단의 지갑 정보 또는 연결된 지갑에서 잔액을 확인하세요.
