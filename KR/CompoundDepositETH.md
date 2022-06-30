```meta-Currency
```

# Compound에 ETH 예금하기

Chainrunner Q는 이 문서의 내용대로 Compound에서 ETH를 예금합니다.

### 예금할 금액 설정하기

- 예금할 금액을 설정합니다.

```input ETH
// 예금할 ETH 수량
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(getBalance() >= amountIn, "보유한 ETH가 부족합니다.");
```

### 설정 한 금액 예금하기

- 설정한 금액만큼 예금합니다.

```taster
Q.compound.deposit("eth", amountIn);
```

### 설정 한 금액을 담보로 설정하기

- 예금한 자산을 담보로 잡을 수 있도록 활성화합니다. 이후 활성화된 예금을 담보로 대출 받을 수 있습니다.
- 예금만 한다면 이 단계는 생략해도 되고, 담보 활성화 여부는 [Compound](https://app.compound.finance/)에서 수정 가능합니다.

```taster
Q.compound.setUseReserveAsCollateral("eth", true);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 예금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [Compound](https://app.compound.finance/) 에서 확인할 수 있습니다.
