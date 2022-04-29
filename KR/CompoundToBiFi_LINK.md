```meta-Currency
link
```

# Compound에서 BiFi로 LINK 자산 옮기기

Chainrunner Q는 이 문서의 내용대로 Compound에 있는 나의 LINK 예금을 BiFi로 옮깁니다.

### Compound에 예금된 LINK를 확인합니다.

- 반드시 예금된 LINK 수량을 확인하시고, 다음 step을 진행하세요.
- 예금을 담보로 사용하고 있는 경우, 출금이 제한될 수 있습니다. [Compound](https://app.compound.finance/)에서 가능 여부를 확인하세요.

```output-Dynamic
// Compound에 예금된 LINK의 양을 확인합니다
let assetAmount = Q.compound.getDepositAssetAmount ("link");
assert (assetAmount >= 0.000001 link, "Compound에 LINK 예금이 없거나 너무 작습니다.");
print ("LINK 예금량:" + assetAmount.toString());
```

### Compound에 예금된 LINK를 출금합니다.

```taster
// Compound에서 LINK를 출금합니다
Q.compound.withdraw ("link", assetAmount);
```

### 출금한 LINK를 BiFi에 다시 예금합니다.

```taster
// BiFi에 LINK를 다시 예금합니다
Q.bifi.deposit ("link", assetAmount);
print (assetAmount.toString () + " 를 Compound에서 BiFi로 옮겼습니다.");
```

### 모든 Step이 정상적으로 완료되었습니다.

- Compound 예금이 BiFi로 이동했습니다.
- 자세한 예금 및 대출 현황은 [BiFi App](https://app.bifi.finance/) 페이지에서 확인할 수 있습니다.
