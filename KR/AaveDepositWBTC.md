```meta-Currency
wbtc
```

# AAVE에 WBTC 예금하기

다음 과정은 AAVE V2에 WBTC를 예금합니다. 해당 서비스는 Aave의 상태에 따라서 사용이 제한될 수 있습니다.

### 예금할 금액 설정하기

- 예금할 금액을 설정합니다.

```input WBTC
// 예금할 WBTC 수량
let amountIn = 0.01;
```

```input-Verify
assert(L2Lending.aaveV2.getIsActive("wbtc") && !L2Lending.aaveV2.getIsFrozen("wbtc"), "시장 설정으로 인해 현재 예금할 수 없습니다.");
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(Q.Token.balanceOf("wbtc") >= amountIn, "보유한 WBTC가 부족합니다.");
```

### 설정한 금액 예금하기

- 설정한 금액만큼 예금합니다.

```taster
Q.aaveV2.deposit("wbtc", amountIn);
```

### 예금을 담보로 설정하기

- 예금한 자산을 담보로 잡을 수 있도록 활성화합니다. 이후 활성화된 예금을 담보로 대출 받을 수 있습니다.
- 예금만 한다면 이 단계는 생략해도 되고, 담보 활성화 여부는 [AAVE](https://app.aave.com/#/dashboard)에서 수정 가능합니다.

```taster
Q.aaveV2.setUseReserveAsCollateral("wbtc", true);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 예금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [AAVE](https://app.aave.com/#/dashboard)에서 확인할 수 있습니다.
