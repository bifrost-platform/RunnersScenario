```meta-Currency
usdt
```

# Venus에 USDT 예금하기

Chainrunner Q는 이 문서의 내용대로 Venus에 USDT를 예금합니다.

### 예금할 금액 설정하기

- 예금할 금액을 설정합니다.

```input USDT
// 예금할 USDT 수량
let amountDeposit = 100;
```

```input-Verify
assert(amountDeposit > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountDeposit), "잘못된 형식의 값 입니다.");
assert(Q.Token.balanceOf("usdt") >= amountDeposit, "보유한 USDT가 부족합니다.");
```

### 설정한 금액 예금하기

- 설정한 금액만큼 예금합니다.

```taster
Q.venus.deposit("usdt", amountDeposit);
```

### 설정한 금액을 담보로 설정하기

- 예금한 자산을 담보로 설정하고 Venus에서 대출 받을 수 있습니다.
- 예금만 한다면 이 단계는 생략해도 됩니다. 담보 활성화 여부는 [Venus](https://app.venus.io/dashboard)에서 수정 가능합니다.

```taster
Q.venus.setUseReserveAsCollateral("usdt", true);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 예금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Venus](https://app.venus.io/dashboard)에서 확인할 수 있습니다.
