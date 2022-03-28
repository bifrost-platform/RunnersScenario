```meta-Currency
kwbtc
```

# BiFi X에서 KWBTC 레버리지 포지션 잡기

Chainrunner Q는 이 문서의 내용대로, BiFi X에서 KWBTC를 최대 배율로 레버리지하고, KUSDC를 이용해 롱 포지션을 간편하게 잡을 수 있도록 합니다.

### 사용할 KWBTC를 입력합니다.

```input KWBTC
let amount = 0.001;
```

```input-Verify
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(amount <= Q.Token.balanceOf ("kwbtc"), "잔액이 부족합니다.");
assert(Q.bifiX.isBetLiquidityEnough("kwbtc", "kusdc", amount, Q.bifiX.getMaxBoost("kwbtc")), "유동성이 부족합니다. 금액을 줄여주세요.");
```

### BiFi X에서 KWBTC를 최대 배율로 레버리지하고 롱 포지션을 잡습니다.

- 슬리피지 값(0.5%)을 사용합니다.

```taster
// BiFi X에서 레버리지 할 수 있는 KWBTC의 최대 배율을 확인합니다
let maxBoost = Q.bifiX.getMaxBoost ("kwbtc");

// BiFi X가 사용할 KWBTC를 가져갈 수 있도록 허락합니다.
Q.bifiX.approve("kwbtc", amount);

// 최대 배율로 포지션을 생성합니다
let ok = Q.bifiX.bet("kwbtc", "kusdc", amount, maxBoost);
assert(ok, "현재 BiFi X를 사용할 수 없습니다. 잠시 후 다시 시도해주세요.");
```

### 모든 단계를 정상적으로 완료했습니다.

- 이제 BiFi X 서비스로 이동해, 생성한 포지션을 확인하세요. [바이파이 X 서비스로 이동](https://x.bifi.finance/)
