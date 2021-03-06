```meta-Currency
btcb
```

# BiFi에서 BTCB 출금하기

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/) 는 다양한 네트워크에서 Lending 서비스를 지원합니다.
Chainrunner Q는 이 문서의 내용대로 BiFi에 예금한 BTCB를 출금합니다.

### 출금 가능한 최대 금액 확인하기

- 출금 가능한 최대 금액을 확인합니다.

```output-Dynamic
let amountWithdrawMax = Q.bifi.getWithdrawableAmount("btcb");
assert(amountWithdrawMax > 0.000001 btcb, "출금 가능한 금액이 너무 적습니다.");
print("출금 가능한 금액: " + amountWithdrawMax.toString());
```

### 출금할 금액 설정하기

- 출금할 금액을 설정합니다.

```input BTCB
// 출금할 BTCB 수량
let amountWithdraw = 0.01;
```

```input-Verify
assert(amountWithdraw > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountWithdraw), "잘못된 형식의 값이 입력 되었습니다.");
assert(Q.bifi.getWithdrawableAmount("btcb") >= amountWithdraw, "출금 가능한 BTCB가 부족합니다.");
```

### 설정한 금액 출금하기

- 설정한 금액만큼을 BiFi에 출금합니다.

```taster
Q.bifi.withdraw("btcb", amountWithdraw);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 출금이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/)에서 확인할 수 있습니다.
