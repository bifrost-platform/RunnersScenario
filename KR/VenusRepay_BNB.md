```meta-Currency
```

# Venus에서 BNB 상환하기

Chainrunner Q는 이 문서의 내용대로 Venus에서 대출한 BNB를 상환합니다.

### 상환 가능한 최대 금액 확인하기

- 상환 가능한 최대 금액을 확인합니다.

```output-Dynamic
let amountRepayMax = Q.venus.getAmountRepayMax("bnb");
assert(amountRepayMax > 0.000001 bnb, "상환 가능한 금액이 너무 적습니다.");
print("상환 가능한 금액: " + amountRepayMax.toString());
```

### 상환할 금액 설정하기

- 상환할 금액을 설정합니다.

```input BNB
// 상환할 BNB 수량
let amountRepay = 1.0;
```

```input-Verify
assert(amountRepay > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountRepay), "잘못된 형식의 값 입니다.");
assert(getBalance() >= amountRepay, "상환할 BNB가 부족합니다.");
assert(amountRepayMax >= amountRepay, "부채보다 많은 금액을 상환할수 없습니다.");
```

### 설정 한 금액 상환하기

- 설정한 금액만큼 상환합니다.

```taster
Q.venus.repay("bnb", amountRepay);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 상환이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Venus](https://app.venus.io/dashboard)에서 확인할 수 있습니다.
