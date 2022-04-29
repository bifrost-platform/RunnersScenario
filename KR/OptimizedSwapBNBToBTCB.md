```meta-Currency
btcb
```

# BNB를 BTCB로 교환하기

Chainrunner Q는 이 문서의 내용대로 최적의 DEX에서 BNB를 BTCB로 교환합니다.

### 최적의 DEX를 찾습니니다.

- ChainRunner에서 지원하는 DEX들 중에서 가장 많은 수량을 교환해주는 DEX를 찾습니다.
- 이번 Step에서는 1 BNB를 기준으로 교환 가능한 수량을 DEX별로 보여줍니다.
- DEX에서 구매가능한 수량 부족시 최대 구매가능 BTCB의 수량만 표시됩니다.

```output-Dynamic
let outputs = Q.optimizedSwap.bsc.getOutputs("btcb", 1 bnb);
let target = Q.optimizedSwap.getBest (outputs);
let (bestAmount, target) = outputs[0];
print("최적 DEX는 " + target + " 입니다. (" + bestAmount.toString() + ")\n");
print ("\n최적 DEX 대비 손익 비교\n");
print ("\n현재 체인 : \n");
Q.optimizedSwap.printOutputs (bestAmount, outputs);
print ("\n다른 체인 : ");
Q.optimizedSwap.bsc.printOtherChainOutputs (bestAmount, "btcb", 1 bnb);
```

### 교환할 BNB의 수량을 입력합니다.

- 입력된 BNB로 구매 가능한 BTCB의 수량이 자동 계산됩니다.
- BNB를 많이 입력하더라도, 실제 구매에 사용된 BNB만 소비됩니다.

```input-Dynamic BNB
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountIn <= getBalance (), "BNB 잔액이 부족합니다.");
```

```output-Dynamic BTCB
Q.optimizedSwap.bsc.getOutput (target, "btcb", amountIn);
```

### 최적의 DEX에서 BNB를 BTCB로 교환합니다.

- 슬리피지 값은 (0.5%)을 사용합니다.

```taster
// BNB를 BTCB로 교환합니다.
Q.optimizedSwap.bsc.swap (target, "btcb", amountIn);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 좌측 상단의 지갑 정보 또는 연결된 지갑에서 잔액을 확인하세요.
