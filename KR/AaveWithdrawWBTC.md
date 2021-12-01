```meta-Currency
wbtc
```

# AAVE에서 WBTC 출금하기

다음 과정은 AAVE V2에서 예금된 WBTC를 출금합니다.

### 출금 가능한 최대 금액 확인

- 대출 가능한 WBTC의 최대 수량을 확인합니다.
- 정확한 액수는 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.

```output-Dynamic
let amountWithdrawMax = Q.aaveV2.getAmountWithdrawMax("wbtc");
assert(amountWithdrawMax > 0.000001 wbtc, "출금 가능한 금액이 너무 적습니다.");
print("출금 가능한 금액: " + amountWithdrawMax.toString());
```

### 출금할 금액 설정하기

- 출금할 금액을 설정합니다.

```input WBTC
// 출금할 wbtc 수량
let amountOut = 0.01;
```

```input-Verify
assert(amountOut > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountOut), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountWithdrawMax >= amountOut, "예금된 WBTC가 부족합니다.");
```

### 설정한 금액 출금하기

- 설정한 금액만큼 출금합니다.

```taster
Q.aaveV2.withdraw("wbtc", amountOut);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 출금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.