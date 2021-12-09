```meta-Currency
usdt
```

# AAVE에서 USDT 출금하기

다음 과정은 AAVE V2에서 예금된 USDT를 출금합니다. 해당 서비스는 Aave의 상태에 따라서 사용이 제한될 수 있습니다.

### 출금 가능한 최대 금액 확인

- 출금 가능한 USDT의 최대 수량을 확인합니다.
- 정확한 액수는 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.

```output-Dynamic
assert(Q.aaveV2.getIsActive("usdt"), "시장 설정으로 인해 현재 출금할 수 없습니다.");
let amountWithdrawMax = Q.aaveV2.getAmountWithdrawMax("usdt");
assert(amountWithdrawMax > 0.000001 usdt, "출금 가능한 금액이 너무 적습니다.");
print("출금 가능한 금액: " + amountWithdrawMax.toString());
```

### 출금할 금액 설정하기

- 출금할 금액을 설정합니다.

```input USDT
// 출금할 USDT 수량
let amountOut = 100;
```

```input-Verify
assert(amountOut > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountOut), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountWithdrawMax >= amountOut, "예금된 USDT가 부족합니다.");
```

### 설정한 금액 출금하기

- 설정한 금액만큼 출금합니다.

```taster
Q.aaveV2.withdraw("usdt", amountOut);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 출금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.
