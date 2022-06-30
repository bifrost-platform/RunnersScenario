```meta-Currency
usdt
```

# Venus에서 USDT 대출하기

Chainrunner Q는 이 문서의 내용대로 Venus에서 USDT를 대출합니다.

### 대출 가능한 최대 금액 확인하기

- 대출 가능한 최대 금액을 확인합니다.

```output-Dynamic
let amountBorrowMax = Q.venus.getBorrowableAmount("usdt");
assert(amountBorrowMax > 0.000001 usdt, "대출 가능한 금액이 너무 적습니다.");
print("대출 가능한 금액: " + amountBorrowMax.toString());
```

### 대출할 금액 설정하기

- 대출할 금액을 설정합니다.

```input USDT
// 대출할 USDT 수량
let amountBorrow = 100;
```

```input-Verify
assert(amountBorrow > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountBorrow), "잘못된 형식의 값 입니다.");
assert(amountBorrowMax >= amountBorrow, "빌릴 수 있는 USDT가 부족합니다.");
```

### 설정한 금액 대출하기

- 설정한 수량만큼 대출합니다.
- 서비스의 특성상 대출 가능한 수치를 벗어나면, 성공 여부를 정확히 알려주지 않고 종료될 수 있습니다.
- 정확한 대출 수량과 대출 성공 여부는 [Venus](https://app.venus.io/dashboard)에서 다시 한번 확인하세요.

```taster
Q.venus.borrow("usdt", amountBorrow);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 대출이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Venus](https://app.venus.io/dashboard)에서 확인할 수 있습니다.
