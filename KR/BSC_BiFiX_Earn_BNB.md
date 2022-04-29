```meta-Currency
bifib
```

# BiFi-X에서 BNB Earn하기

BiFi 서비스는 사용자별로 예금과 대출량에 비례하여 "VIP 포인트"와 같은 보상토큰(BiFi 토큰)을 지급합니다.
보상토큰을 얻으려는 투자자는 더 많은 예금과 대출을 실행하여 높은 보상토큰 수익률을 기대할 것입니다.
이런 투자자는 BiFi-X의 Earn 서비스를 활용하여 적은 초기 자금으로 보상토큰 수익률을 극대화 할 수 있습니다.

Chainrunner Q는 이 문서의 내용대로, BNB 토큰을 가지고 BiFi-X Earn 서비스를 간편하게 사용할 수 있도록 합니다.

### BiFi-X 수수료로 필요한 BiFi 수량이 충분한지 확인합니다.

- BiFi-X 서비스에서는 BiFi가 수수료로 발생합니다. 수수료로 지불할 BiFi 수량을 확보하고 있어야 합니다.

```output-Dynamic
let bifiFee = Q.bifiX.getFee ();
let bifiBalance = Q.Token.balanceOf ("bifib");
assert(bifiBalance >= bifiFee, "BiFi 수량이 부족합니다.");
print ("수수료로 필요한 BiFi 수량: " + bifiFee.toString ());
```

### 사용할 BNB를 입력 받습니다.

```input BNB
let amount = 1;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount <= getBalance (), "BNB 잔액이 부족합니다.");
```

### BiFi-X에서 수수료로 BiFi를 지불할 수 있도록 승인해 줍니다.

```taster
Q.bifiX.approve("bifib", bifiFee);
```

### BiFi-X에 BNB를 최대 배율로 레버리지하고 Earn을 합니다.

```taster
// BiFi-X에서 레버리지 할 수 있는 BNB의 최대 배율을 확인합니다
let maxBoost = Q.bifiX.getMaxBoost ("bnb");

// Earn 포지션을 생성합니다
Q.bifiX.earn("bnb", amount, maxBoost);
```

### 모든 step이 정상적으로 완료되었습니다.

- 이제 BiFi-X 서비스로 이동하여, 생성된 포지션을 확인하세요. [바이파이 X 서비스로 이동](https://x.bifi.finance/)
