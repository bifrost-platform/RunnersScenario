```meta-Currency
oeth
```

# BiFi X에서 oETH 롱 포지션 잡기

Chainrunner Q는 이 문서의 내용대로, BiFi X에서 oETH를 최대 배율로 레버리지하고, oUSDC를 이용해 롱 포지션을 간편하게 잡을 수 있도록 합니다.

### 사용할 oETH를 입력합니다.

```input oETH
let amount = 0.1;
```

```input-Verify
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(amount <= Q.Token.balanceOf ("oeth"), "잔액이 부족합니다.");
assert(Q.bifiX.isBetLiquidityEnough("oeth", "ousdc", amount, Q.bifiX.getMaxBoost("oeth")), "유동성이 부족합니다. 금액을 줄여주세요.");
```

### BiFi X에서 oETH를 최대 배율로 레버리지하고 롱 포지션을 잡습니다.

- 슬리피지 값(0.5%)을 사용합니다.

```taster
// BiFi X에서 레버리지 할 수 있는 oETH의 최대 배율을 확인합니다
let maxBoost = L2Lending.bifiX.getMaxBoost ("oeth");

// BiFi X가 사용할 oETH를 가져갈 수 있도록 허락합니다.
Q.bifiX.approve("oeth", amount);

// 최대 배율로 포지션을 생성합니다
let ok = Q.bifiX.bet("oeth", "ousdc", amount, maxBoost);
assert(ok, "현재 BiFi X를 사용할 수 없습니다. 잠시 후 다시 시도해주세요.");
```

### 모든 단계를 정상적으로 완료했습니다.

- 이제 BiFi X 서비스로 이동해, 생성한 포지션을 확인하세요. [바이파이 X 서비스로 이동](https://x.bifi.finance/)
