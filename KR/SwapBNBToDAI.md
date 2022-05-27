```meta-Currency
dai
```

# Sushiswap에서 BNB를 DAI로 교환하기

Chainrunner Q는 이 문서의 내용대로 Sushiswap에서 BNB를 DAI로 교환합니다.

### 교환할 BNB의 수량을 입력합니다.

- 입력된 BNB로 구매 가능한 DAI의 수량이 자동 계산됩니다.
- 많은 양의 BNB를 입력하더라도, DEX(Sushiswap)에서 구매가능한 수량 부족시 최대 구매가능 DAI의 수량만 표시됩니다.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountIn <= getBalance(), "BNB 잔액이 부족합니다.");
```

```output-Dynamic DAI
let daiAmount = Q.sushi.getAmountsOutFromExactIn("dai", amountIn);
print(daiAmount);
```

### Sushiswap에서 BNB를 DAI로 교환합니다.

- Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
// BNB를 DAI로 교환합니다.
Q.sushi.swapExactBNBForTokens("dai", amountIn);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 좌측 상단의 지갑 정보 또는 연결된 지갑에서 잔액을 확인하세요.
