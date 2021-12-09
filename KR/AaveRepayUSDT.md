```meta-Currency
usdt
```

# AAVE에서 대출한 USDT 상환하기

다음 과정은 AAVE V2에서 대출한 USDT를 상환합니다. 해당 서비스는 Aave의 상태에 따라서 사용이 제한될 수 있습니다.

### 상환 가능한 금액 확인하기

- AAVE는 이자 계산 방식에 따라 고정금리(stable) 대출과 변동금리(variable) 대출을 지원합니다. 기존 대출의 이자 계산 방식을 선택하고, 상환해야 하는 최대 수량을 확인합니다. 자세한 이자 계산 방식은 [여기](https://docs.aave.com/faq/borrowing#what-is-the-difference-between-stable-and-variable-rate)에서 확인할 수 있습니다.

- 고정금리(stable): 1
- 변동금리(varialbe): 2

```input-Dynamic
// 이자 계산 방식
let interestRateMode = 1;
```

```input-Verify
assert(interestRateMode == 1 || interestRateMode == 2, "잘못된 이자 계산 방식입니다.");
```

```output-Dynamic
assert(Q.aaveV2.getIsActive("usdt"), "시장 설정으로 인해 현재 상환할 수 없습니다.");
let amountRepayMax = Q.aaveV2.getAmountRepayMax("usdt", interestRateMode);
assert(amountRepayMax > 0.000001 usdt, "상환 가능한 금액이 너무 적습니다.");
print("상환 가능한 금액: " + amountRepayMax.toString());
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
assert(Q.erc20.balanceOf("usdt") >= amount, "상환할 수 있는 USDT가 부족합니다.");
assert(amountRepayMax >= amount, "부채보다 많은 금액을 상환할수 없습니다.");
```

### 설정 한 금액 상환하기

- 설정한 금액만큼 상환합니다.

```taster
Q.aaveV2.repay("usdt", amount, interestRateMode);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 상환이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.
