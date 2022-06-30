```meta-Currency
```

# AAVE V2에서 BiFi로 ETH 자산 옮기기

다음 과정에서 AAVE V2에 예금된 ETH를 출금하고, 곧바로 BiFi로 옮깁니다. 해당 서비스는 Aave의 상태에 따라서 사용이 제한될 수 있습니다.

### AAVE V2에 예금된 ETH를 확인합니다.

- 반드시 예금된 ETH 수량을 확인하시고, 다음 step을 진행하세요.
- 예금을 담보로 사용하고 있는 경우, 출금이 제한될 수 있습니다. [AAVE](https://app.aave.com/#/dashboard)에서 가능 여부를 확인하세요.

```output-Dynamic
assert(L2Lending.aaveV2.getIsActive("eth"), "시장 설정으로 인해 현재 출금할 수 없습니다.");
// AAVE에 예금된 ETH의 양을 확인합니다
let assetAmount = Q.aaveV2.getDepositedAmount ("eth");
assert (assetAmount >= 0.000001 ether, "AAVE v2에 ETH 예금이 없거나 너무 작습니다.");
print ("ETH 예금량:" + assetAmount.toString());
```

### AAVE V2에 예금된 ETH를 출금합니다.

```taster
// AAVE에서 ETH를 출금합니다
Q.aaveV2.withdraw ("eth", assetAmount);
```

### 출금한 ETH를 BiFi에 다시 예금합니다.

```taster
// BiFi에 ETH를 다시 예금합니다
Q.bifi.deposit ("eth", assetAmount);
print (assetAmount.toString () + " 를 AAVE에서 BiFi로 옮겼습니다.");
```

### 모든 Step이 정상적으로 완료되었습니다.

- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/) 페이지에서 확인할 수 있습니다.
