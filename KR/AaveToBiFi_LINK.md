```meta-Currency
link
```

# AAVE V2에서 BiFi로 LINK 자산 옮기기

다음 과정에서 AAVE V2에 예금된 LINK를 출금하고, 곧바로 BiFi로 옮깁니다.

### AAVE V2에 예금된 LINK를 확인합니다.

- 반드시 예금된 LINK 수량을 확인하시고, 다음 step을 진행하세요.
- 예금을 담보로 사용하고 있는 경우, 출금이 제한될 수 있습니다. [AAVE](https://app.aave.com/#/dashboard)에서 가능 여부를 확인하세요.

```output-Dynamic
// AAVE에 예금된 LINK의 양을 확인합니다
let assetAmount = Q.aaveV2.getUserReserve ("link");
assert (assetAmount >= 0.000001 link, "AAVE v2에 LINK 예금이 없거나 너무 작습니다.");
print ("LINK 예금량:" + assetAmount.toString());
```

### AAVE V2에 예금된 LINK를 출금합니다.

```taster
// AAVE에서 LINK를 출금합니다
Q.aaveV2.withdraw ("link", assetAmount);
```

### 출금한 LINK를 BiFi에 다시 예금합니다.

```taster
// BiFi에 LINK를 다시 예금합니다
bifi.token.deposit ("link", assetAmount);
print (assetAmount.toString () + " 를 AAVE에서 BiFi로 옮겼습니다.");
```

### 모든 Step이 정상적으로 완료되었습니다.

- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/) 페이지에서 확인할 수 있습니다.
