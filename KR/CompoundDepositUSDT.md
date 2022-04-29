```meta-Currency
usdt
```

# Compound에 USDT 예금하기

Chainrunner Q는 이 문서의 내용대로 Compound에서 USDT를 예금합니다.

### 예금할 금액 설정하기

- 예금할 금액을 설정합니다.

```input USDT
// 예금할 USDT 수량
let amountIn = 100;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(Q.Token.balanceOf("usdt") >= amountIn, "보유한 USDT가 부족합니다.");
```

### 설정 한 금액 예금하기

- 설정한 금액만큼 예금합니다.

```taster
Q.compound.deposit("usdt", amountIn);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 예금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Compound](https://app.compound.finance/)에서 확인할 수 있습니다.
