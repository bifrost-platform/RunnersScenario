```meta-Currency
usdc
```

# AAVE V2에서 BiFi로 USDC 자산 옮기기

다음 과정에서 AAVE V2에 예금된 USDC를 인출하고, 곧바로 BiFi로 옮깁니다.

### AAVE V2에 예금된 USDC를 확인합니다.

- 반드시 예금된 DAI 수량을 확인하시고, 다음 step을 진행하세요.
- 예금을 담보로 사용하고 있는 경우, 출금이 제한될 수 있습니다. [AAVE](https://app.aave.com/#/dashboard)에서 가능 여부를 확인하세요.

```output-Dynamic
// AAVE에 예금된 USDC의 양을 확인합니다
let assetAmount = Q.aaveV2.getUserReserve ("usdc");
assert (assetAmount >= 0.000001 usdc, "AAVE v2에 USDC 예금이 없거나 너무 작습니다.");
print ("USDC 예금량:" + assetAmount.toString());
```

### AAVE V2에 예금된 USDC를 출금합니다.

```taster
// AAVE에서 USDC를 출금합니다
Q.aaveV2.withdraw ("usdc", assetAmount);
```

### 출금한 USDC를 BiFi에 다시 예금합니다.

```taster
// BiFi에 USDC를 다시 예금합니다
bifi.token.deposit ("usdc", assetAmount);
print (assetAmount.toString () + " 를 AAVE에서 BiFi로 옮겼습니다.");
```

### 모든 Step이 정상적으로 완료되었습니다.

- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/) 페이지에서 확인할 수 있습니다.
