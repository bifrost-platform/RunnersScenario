```meta-Currency
kusdc
```

# BiFi에서 KUSDC 상환하기

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

[BiFi](https://bifi.finance/)는 다양한 네트워크에서 Lending 서비스를 지원합니다.
Chainrunner Q는 이 문서의 내용대로 BiFi에서 대출한 KUSDC를 상환합니다.

### 상환 가능한 최대 금액 확인하기

- 상환 가능한 금액을 확인합니다.

```output-Dynamic
let amountRepayMax = Q.bifi.getMaxRepayAmount("kusdc");
assert(amountRepayMax > 0.000001 kusdc, "상환 가능한 금액이 너무 적습니다.");
print("상환 가능한 금액: " + amountRepayMax.toString());
```

### 상환할 금액 설정하기

- 상환할 금액을 설정합니다.

```input KUSDC
// 상환할 KUSDC 수량 (소수점도 가능합니다.)
let amountRepay = 100;
```

```input-Verify
assert(amountRepay > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountRepay), "잘못된 형식의 값이 입력 되었습니다.");
assert(Q.kip7.balanceOf("kusdc") >= amountRepay, "상환할 수 있는 KUSDC가 부족합니다.");
assert(Q.bifi.getMaxRepayAmount("kusdc") >= amountRepay, "부채보다 많은 금액을 상환할수 없습니다.");
```

### 설정한 금액 상환하기

- 설정한 금액만큼을 BiFi에 상환합니다.

```taster
Q.bifi.repay("kusdc", amountRepay);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 상환이 완료되었습니다.
- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/)에서 확인할 수 있습니다.
