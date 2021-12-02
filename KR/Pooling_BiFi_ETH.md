```meta-Currency
bifi, 0x0beC54c89a7d9F15C4e7fAA8d47ADEdF374462eD
```

# BiFi Pooling에 BiFi-WETH LP 토큰 예금하기

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

SushiswapV2 BiFi-WETH 풀에 유동성을 공급한 사용자는 LP(Liquidity Provider) 토큰을 지급 받습니다.
BiFi 서비스는 이렇게 유동성을 공급하여 BiFi 생태계 발전에 기여한 사용자들에게 보상 토큰으로 BiFi를 지급합니다.
Chainrunner Q는 Pool에 유동성을 제공하고, 받은 LP 토큰을 BiFi 서비스에 풀링하는 복잡한 과정을 아주 간단하게 실행할 수 있도록 합니다.

### 사용할 ETH를 입력 받습니다.

- 사용자가 설정한 ETH 수량의 절반을 BiFi로 바꾸어 SushiswapV2의 BiFi-WETH 풀에 유동성을 공급하고, 그에 대한 LP 토큰을 BiFi에 풀링하겠습니다.
- WETH(Wrapped ETH)는 ETH를 ERC20 토큰과 교환하기 위해 만들어진 ERC20 토큰입니다. Sushiswap에서는 BiFI-ETH 유동성을 공급하기 위해 BiFI-WETH 풀을 제공합니다.

```input ETH
// ETH 수량을 결정해주세요.
let amount = 0.1;
```

```input-Verify
assert(amount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (amount), "잘못된 형식의 값이 입력 되었습니다.");
assert(amount <= getBalance (), "ETH 잔액이 부족합니다." );
```

### Sushiswap에서 ETH를 BiFi로 교환하겠습니다.

- Sushiswap 풀에 유동성을 제공하기 위해 사용 될 BiFi를 교환합니다. Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
// ETH 수량의 절반을 BiFi로 교환합니다
let bifiAmount = Q.sushi.swapExactETHForTokens ("bifi", amount / 2);
assert (bifiAmount > 0, "BiFi 잔액이 0입니다.");
```

### Sushiswap의 BiFi-WETH 풀에 유동성을 추가합니다.

- Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
let lpAmount = Q.sushi.addLiquidityETH ("bifi", bifiAmount, amount / 2);
assert (lpAmount > 0, "유동성 토큰 잔액이 0입니다.");
```

### 이제, LP 토큰을 BiFi에 풀링하도록 하겠습니다. BiFi에 Sushiswap의 LP 토큰을 풀링하면, BiFi 토큰을 보상으로 지급합니다.

```taster
// 이제, LP 토큰을 BiFi에 풀링하겠습니다.
Q.bifi.depositLp ("bifi", lpAmount);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 이제 BiFi 서비스로 이동하여, 예금 상황을 확인하세요. [바이파이 서비스로 이동](https://app.bifi.finance/pool/sushiswap/bifiEth?chainid=mainnet)
