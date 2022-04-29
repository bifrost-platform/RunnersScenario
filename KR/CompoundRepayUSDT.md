```meta-Currency
usdt
```

# Compound에서 USDT 상환하기

Chainrunner Q는 이 문서의 내용대로 Compound에서 대출한 USDT를 상환합니다.

### 상환 가능한 최대 금액 확인하기

- 상환 가능한 최대 금액을 확인합니다.

```output-Dynamic
let amountRepayMax = Q.compound.getRepayAmount ("usdt");
assert (amountRepayMax >= 0.000001 usdt, "상환 가능한 금액이 너무 적습니다.");
print ("상환 가능한 금액: " + amountRepayMax.toString ());
```

### 상환할 금액 설정하기

- 상환할 금액을 설정합니다.

```input USDT
// 상환할 USDT 수량
let amount = 100;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(Q.Token.balanceOf("usdt") >= amount, "상환할 USDT가 부족합니다.");
assert(amountRepayMax >= amount, "부채보다 많은 금액을 상환할수 없습니다.");
```

### 설정한 금액 상환하기

- 설정한 금액만큼 상환합니다.

```taster
Q.compound.repay("usdt", amount);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 상환이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Compound](https://app.compound.finance/)에서 확인할 수 있습니다.
