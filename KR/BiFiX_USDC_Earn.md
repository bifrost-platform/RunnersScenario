```meta-Currency
bifi, usdc
```

# BiFi-X에서 USDC Earn하기

BiFi 서비스는 사용자별로 예금과 대출량에 비례하여 "VIP 포인트"와 같은 보상토큰(BiFi 토큰)을 지급합니다.
보상토큰을 얻으려는 투자자는 더 많은 예금과 대출을 실행하여 높은 보상토큰 수익률을 기대할 것입니다.
이런 투자자는 BiFi-X의 Earn 서비스를 활용하여 적은 초기 자금으로 보상토큰 수익률을 극대화 할 수 있습니다.

Chainrunner Q는 이 문서의 내용대로, USDC 토큰을 가지고 BiFi-X Earn 서비스를 간편하게 사용할 수 있도록 합니다.

### 사용할 ETH를 입력 받습니다.

```input ETH
let amount = 1;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount <= getBalance (), "ETH 잔액이 부족합니다." );
```

### Sushiswap에서 ETH를 USDC로 교환합니다.

- Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
let usdcAmount = Q.sushi.swapExactETHForTokens ("usdc", amount);
```

### Sushiswap에서 ETH를 BiFi로 교환합니다.

- Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
let bifiFee = Q.bifiX.getFee ();
Q.sushi.swapETHForExactTokens ("bifi", bifiFee);
```

### BiFi-X에서 수수료로 BiFi를 지불할 수 있도록 승인해 줍니다.

```taster
Q.bifiX.approveBiFi (bifiFee);
```

### BiFi-X에 USDC를 최대 배율로 레버리지하고 Earn을 합니다.

```taster
// BiFi-X에서 레버리지 할 수 있는 USDC의 최대 배율을 확인합니다
let maxBoost = Q.bifiX.getMaxBoost ("usdc");

// 포지션을 생성하기 앞서, USDC 토큰을 승인합니다.
let usdcTokenAddr = erc20.getTokenAddr ("usdc");
let xFactoryAddr = bifiX.xFactory.getAddress ();
erc20.approve (usdcTokenAddr, xFactoryAddr, usdcAmount);

// Earn 포지션을 생성합니다
Q.bifiX.createEarnPosition ("usdc", usdcAmount, maxBoost);
```

### 모든 step이 정상적으로 완료되었습니다.

- 이제 BiFi-X 서비스로 이동하여, 생성된 포지션을 확인하세요. [바이파이 X 서비스로 이동](https://x.bifi.finance/)
