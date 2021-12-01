```meta-Currency
wbtc
```

# BiFi에 WBTC 예금하기

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) 는 다양한 네트워크에서 Lending 서비스를 지원합니다.
Chainrunner Q는 이 문서의 내용대로 BiFi에 ETH를 예금 합니다.

### 예금할 금액 설정하기

- 예금할 금액을 설정합니다. (보유하신 WBTC가 부족하거나 잘못된 숫자가 입력된 경우에는 에러가 발생합니다.)

```input WBTC
// 예금할 WBTC 수량
let amountDeposit = 0.01;
```

```input-Verify
assert(amountDeposit > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountDeposit), "잘못된 형식의 값이 입력 되었습니다.");
assert(Q.erc20.balanceOf("wbtc") >= amountDeposit, "보유한 WBTC가 부족합니다.");
```

### BiFi에 예금하기

- 설정한 금액만큼을 BiFi에 예금합니다.
```taster
Q.bifi.deposit("wbtc", amountDeposit);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 예금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/)에서 확인할 수 있습니다.
