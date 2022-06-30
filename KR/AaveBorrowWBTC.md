```meta-Currency
wbtc
```

# AAVE에서 WBTC 대출하기

다음 과정은 AAVE V2의 예금을 담보로 WBTC를 대출합니다. 해당 서비스는 Aave의 상태에 따라서 사용이 제한될 수 있습니다.

### 대출 가능한 금액 확인하기

- 대출 가능한 WBTC의 최대 수량을 확인합니다.
- 정확한 액수는 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("wbtc") && !L2Lending.aaveV2.getIsFrozen("wbtc"), "시장 설정으로 인해 현재 대출할 수 없습니다.");
let amountBorrowMax = Q.aaveV2.getBorrowableAmount("wbtc");
assert(amountBorrowMax > 0.000001 wbtc, "대출 가능한 금액이 너무 적습니다.");
print("대출 가능한 금액: " + amountBorrowMax.toString());
```

### 대출할 금액 설정하기

- 대출할 WBTC 수량을 설정합니다.

```input WBTC
// 대출할 WBTC 수량
let amount = 0.01;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountBorrowMax >= amount, "빌릴 수 있는 WBTC가 부족합니다.");
```

### 대출 이자 방식 선택하기

- AAVE는 이자 계산 방식에 따라 고정금리(stable) 대출과 변동금리(variable) 대출을 지원합니다.
- 자세한 이자 계산 방식은 [여기](https://docs.aave.com/faq/borrowing#what-is-the-difference-between-stable-and-variable-rate)에서 확인할 수 있습니다.

- 고정금리(stable): 1
- 변동금리(varialbe): 2

```input
// 대출 이자 방식
let interestRateMode = 1;
```

```input-Verify
assert(interestRateMode == 1 || interestRateMode == 2, "잘못된 이자 계산 방식입니다.");
assert(Q.aaveV2.getBorrowEnabled("wbtc", interestRateMode), "현재 선택한 이자 계산 방식으로 대출할 수 없습니다.");
```

### 설정 한 금액 대출하기

- 설정한 금액만큼 대출합니다.

```taster
Q.aaveV2.borrow("wbtc", amount, interestRateMode);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 대출이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.
