```meta-Currency
```

# BiFi-X에서 KLAY Earn하기

BiFi 서비스는 사용자별로 예금과 대출량에 비례하여 "VIP 포인트"와 같은 보상토큰(BiFi 토큰)을 지급합니다.
보상토큰을 얻으려는 투자자는 더 많은 예금과 대출을 실행하여 높은 보상토큰 수익률을 기대할 것입니다.
이런 투자자는 BiFi-X의 Earn 서비스를 활용하여 적은 초기 자금으로 보상토큰 수익률을 극대화 할 수 있습니다.

Chainrunner Q는 이 문서의 내용대로, KLAY 토큰을 가지고 BiFi-X Earn 서비스를 간편하게 사용할 수 있도록 합니다.

### 사용할 KLAY를 입력 받습니다.

```input KLAY
let amount = 100;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount <= getBalance (), "KLAY 잔액이 부족합니다.");
```

### BiFi-X에 KLAY를 최대 배율로 레버리지하고 Earn을 합니다.

```taster
// BiFi-X에서 레버리지 할 수 있는 KLAY의 최대 배율을 확인합니다
let maxBoost = Q.bifiX.getMaxBoost ("klay");

// Earn 포지션을 생성합니다
let ok = Q.bifiX.earn("klay", amount, maxBoost);
assert(ok, "현재 BiFi X를 사용할 수 없습니다. 잠시 후 다시 시도해주세요.");
```

### 모든 step이 정상적으로 완료되었습니다.

- 이제 BiFi-X 서비스로 이동하여, 생성된 포지션을 확인하세요. [바이파이 X 서비스로 이동](https://x.bifi.finance/)
