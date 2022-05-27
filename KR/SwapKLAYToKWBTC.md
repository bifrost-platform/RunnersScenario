```meta-Currency
kwbtc
```

# KLAYswap에서 KLAY를 KWBTC로 교환하기

Chainrunner Q는 이 문서의 내용대로 KLAYswap에서 KLAY를 KWBTC로 교환합니다.

### 교환할 KLAY의 수량을 입력합니다.

- 입력된 KLAY로 구매 가능한 KWBTC의 수량이 자동 계산됩니다.
- 많은 양의 KLAY를 입력하더라도, DEX(KLAYswap)에서 구매가능한 수량 부족시 최대 구매가능 KWBTC의 수량만 표시됩니다.
- 현재 KLAY/KWBTC 풀이 존재하지 않기 때문에, KSP, KETH, KUSDT 토큰 중 하나를 거쳐 교환합니다.
- Chainrunner Q는 가장 많은 KWBTC 수량을 얻을 수 있는 경로로 토큰을 교환합니다.

```input-Dynamic KLAY
let amountIn = 10;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountIn <= getBalance(), "KLAY 잔액이 부족합니다.");
```

```output-Dynamic KWBTC
let (routingToken, kwbtcAmount) = Q.klay.getKWBTCAmountOutFromExactIn (amountIn);
print(kwbtcAmount);
```

### KLAYswap에서 KLAY를 KWBTC로 교환합니다.

- KLAYswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
// KLAY를 KWBTC로 교환합니다.
Q.klay.exchangeKlayToKWBTCPos (amountIn, routingToken);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 좌측 상단의 지갑 정보 또는 연결된 지갑에서 잔액을 확인하세요.
