```meta-Currency
bifi, 0x0beC54c89a7d9F15C4e7fAA8d47ADEdF374462eD
```

# BiFi Pooling에 BiFi-WETH LP 토큰 예금하기

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

SushiswapV2 BiFi-WETH 풀에 유동성을 공급한 사용자는 LP(Liquidity Provider) 토큰을 지급 받습니다.
BiFi 서비스는 이렇게 유동성을 공급하여 BiFi 생태계 발전에 기여한 사용자들에게 보상 토큰으로 BiFi를 지급합니다.
Chainrunner Q는 Pool에 유동성을 제공하고, 받은 LP 토큰을 BiFi 서비스에 풀링하는 복잡한 과정을 아주 간단하게 실행할 수 있도록 합니다.

### 사용할 BiFi를 입력 받습니다.

- 사용자가 설정한 BiFi와 그와 가치가 같은 ETH로 SushiswapV2의 BiFi-WETH 풀에 유동성을 공급하고, 그에 대한 LP 토큰을 BiFi에 풀링하겠습니다.
- WETH(Wrapped ETH)는 ETH를 ERC20 토큰과 교환하기 위해 만들어진 ERC20 토큰입니다. Sushiswap에서는 BiFI-ETH 유동성을 공급하기 위해 BiFI-WETH 풀을 제공합니다.
- 지갑에 보유중인 BiFi를 확인하고, 서비스에 사용할 수량을 입력합니다.
- 만약, BiFi를 보유하고 있지 않다면, **토큰 구매하기** 메뉴에서 구매 후 이용하시기 바랍니다.

```input BiFi
// BiFi 수량을 결정해주세요.
let bifiAmount = 1000;
```

```input-Verify
assert(bifiAmount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (bifiAmount), "잘못된 형식의 값이 입력 되었습니다.");
assert(bifiAmount <= Q.erc20.balanceOf ("bifi"), "BiFi 잔액이 부족합니다.");
let ethBalance = getBalance ();
let ethAmount = Q.sushi.getETHAmountsOutFromExactIn("bifi", bifiAmount);
assert(ethAmount <= ethBalance, "ETH 잔액이 부족합니다. BiFi의 수량을 낮게 조절하십시요." );
```

### Sushiswap의 BiFi-WETH 풀에 유동성을 추가합니다.

- Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
let lpAmount = Q.sushi.addLiquidityETH ("bifi", bifiAmount, ethAmount);
assert (lpAmount > 0, "유동성 토큰 잔액이 0입니다.");
```

### 이제, LP 토큰을 BiFi에 풀링하도록 하겠습니다. BiFi에 Sushiswap의 LP 토큰을 풀링하면, BiFi 토큰을 보상으로 지급합니다.

```taster
// 이제, LP 토큰을 BiFi에 풀링하겠습니다.
Q.bifi.depositLp ("bifi", lpAmount);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 이제 BiFi 서비스로 이동하여, 예금 상황을 확인하세요. [바이파이 서비스로 이동](https://app.bifi.finance/pool/sushiswap/bifiEth?chainid=mainnet)
