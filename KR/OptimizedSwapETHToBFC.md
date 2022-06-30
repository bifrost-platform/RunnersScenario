```meta-Currency
bfc
```

# ETH를 BFC로 교환하기

Chainrunner Q는 이 문서의 내용대로 최적의 DEX에서 ETH를 BFC로 교환합니다.

![title](/imgs/ETHtoBFC.jpg)

### 최적의 DEX를 찾습니니다.

- ChainRunner에서 지원하는 DEX들 중에서 가장 많은 수량을 교환해주는 DEX를 찾습니다.
- 이번 Step에서는 1 이더를 기준으로 교환 가능한 수량을 DEX별로 보여줍니다.
- DEX에서 구매가능한 수량 부족시 최대 구매가능 BFC의 수량만 표시됩니다.

```output-Dynamic
let outputs = Q.optimizedSwap.getAmountOuts("eth", "bfc", 1 eth);
Q.optimizedSwap.checkOutputs (outputs);
let (bestAmount, target) = outputs[0];
print("최적 DEX는 " + target + " 입니다. (" + bestAmount.toString() + ")\n");
print ("\n최적 DEX 대비 손익 비교\n");
print ("\n현재 체인 : \n");
Q.optimizedSwap.printOutputs (bestAmount, outputs);
print ("\n다른 체인 : ");
Q.optimizedSwap.printOtherOutputs (bestAmount, "eth", "bfc", 1 eth);
```

### 교환할 ETH의 수량을 입력합니다.

- 입력된 ETH로 구매 가능한 BFC의 수량이 자동 계산됩니다.
- ETH를 많이 입력하더라도, 실제 구매에 사용된 ETH만 소비됩니다.

```input-Dynamic ETH
let amountIn = 0.1;
```

```input-Verify
assert(amountIn > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency(amountIn), "잘못된 형식의 값이 입력 되었습니다.");
assert(amountIn <= getBalance(), "ETH 잔액이 부족합니다.");
```

```output-Dynamic BFC
Q.optimizedSwap.getAmountOut (target, "eth", "bfc", amountIn);
```

### 최적의 DEX에서 ETH를 BFC로 교환합니다.

- 슬리피지 값은 (0.5%)을 사용합니다.

```taster
// ETH를 BFC로 교환합니다.
Q.optimizedSwap.swap (target, "eth", "bfc", amountIn);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 좌측 상단의 지갑 정보 또는 연결된 지갑에서 잔액을 확인하세요.
