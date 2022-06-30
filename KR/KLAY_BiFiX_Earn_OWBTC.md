```meta-Currency
owbtc
```

# BiFi-X에서 oWBTC Earn하기

BiFi 서비스는 사용자별로 예금과 대출량에 비례하여 "VIP 포인트"와 같은 보상토큰(BiFi 토큰)을 지급합니다.
보상토큰을 얻으려는 투자자는 더 많은 예금과 대출을 실행하여 높은 보상토큰 수익률을 기대할 것입니다.
이런 투자자는 BiFi-X의 Earn 서비스를 활용하여 적은 초기 자금으로 보상토큰 수익률을 극대화 할 수 있습니다.

Chainrunner Q는 이 문서의 내용대로, oWBTC 토큰을 가지고 BiFi-X Earn 서비스를 간편하게 사용할 수 있도록 합니다.

### 사용할 oWBTC를 입력 받습니다.

- 지갑에 보유중인 oWBTC를 확인하고, 서비스에 사용할 수량을 입력합니다.
- 만약, oWBTC를 보유하고 있지 않다면, **토큰 구매하기** 메뉴에서 구매 후 이용하시기 바랍니다.

```input oWBTC
let amount = 0.001;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount <= Q.Token.balanceOf ("owbtc"), "oWBTC 잔액이 부족합니다.");
```

### BiFi-X에 oWBTC를 최대 배율로 레버리지하고 Earn을 합니다.

```taster
// BiFi-X에서 레버리지 할 수 있는 oWBTC의 최대 배율을 확인합니다
let maxBoost = L2Lending.bifiX.getMaxBoost ("owbtc");

// 포지션을 생성하기 앞서, oWBTC 토큰을 승인합니다.
Q.bifiX.approve("owbtc", amount);

// Earn 포지션을 생성합니다
let ok = Q.bifiX.earn("owbtc", amount, maxBoost);
assert(ok, "현재 BiFi X를 사용할 수 없습니다. 잠시 후 다시 시도해주세요.");
```

### 모든 step이 정상적으로 완료되었습니다.

- 이제 BiFi-X 서비스로 이동하여, 생성된 포지션을 확인하세요. [바이파이 X 서비스로 이동](https://x.bifi.finance/)
