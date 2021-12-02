```meta-Currency
usdt
```

# Venus에서 USDT 출금하기

Chainrunner Q는 이 문서의 내용대로 Venus에 예금한 USDT를 출금합니다.

### 출금 가능한 최대 금액 확인하기

- 출금 가능한 최대 금액을 확인합니다.
- 정확한 액수는 [Venus](https://app.venus.io/dashboard)에서 직접 확인할 수 있습니다.

```output-Dynamic
let amountWithdrawMax = Q.venus.getAmountWithdrawMax("usdt");
assert(amountWithdrawMax > 0.000001 usdt, "출금 가능한 금액이 너무 적습니다.");
print("출금 가능한 금액: " + amountWithdrawMax.toString());
```

### 출금할 금액 설정하기

- 출금할 금액을 설정합니다.

```input USDT
// 출금할 USDT 수량
let amountWithdraw = 100;
```

```input-Verify
assert(amountWithdraw > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountWithdraw), "잘못된 형식의 값 입니다.");
assert(amountWithdrawMax >= amountWithdraw, "예치된 USDT가 부족합니다.");
```

### 설정한 금액 출금하기

- 설정한 금액만큼 출금합니다.

```taster
Q.venus.withdraw("usdt", amountWithdraw);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 출금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Venus](https://app.venus.io/dashboard)에서 확인할 수 있습니다.
