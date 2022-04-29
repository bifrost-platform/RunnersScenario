```meta-Currency
bfc, 0x281df7fc89294c84afa2a21ffee8f6807f9c9226
```

# BiFi Pooling Contract에 LP 토큰 예치하기

![BiFi Logo](https://s3.ap-northeast-2.amazonaws.com/thebifrost.io/home/bifi/bifi_logo.svg)

SushiswapV2 BFC-WETH 풀에 유동성을 공급한 사용자는 LP(Liquidity Provider) 토큰을 지급 받습니다.
BiFi 서비스는 이렇게 유동성을 공급하여 BiFi 생태계 발전에 기여한 사용자들에게 보상 토큰으로 BiFi를 지급합니다.
Chainrunner Q는 BFC-ETH Pool에 유동성을 제공하고, 받은 LP 토큰을 BiFi 서비스에 풀링하는 복잡한 과정을 아주 간단하게 실행할 수 있도록 합니다.

### 사용할 BFC를 입력 받습니다.

- 사용자가 설정한 BFC와 그와 가치가 같은 ETH로 SushiswapV2의 BFC-WETH 풀에 유동성을 공급하고, 그에 대한 LP 토큰을 BiFi에 풀링하겠습니다.
- WETH(Wrapped ETH)는 ETH를 ERC20 토큰과 교환하기 위해 만들어진 ERC20 토큰입니다. Sushiswap에서는 BFC-ETH 유동성을 공급하기 위해 BFC-WETH 풀을 제공합니다.
- 지갑에 보유중인 BFC를 확인하고, 서비스에 사용할 수량을 입력합니다.
- 만약, BFC를 보유하고 있지 않다면, **토큰 구매하기** 메뉴에서 구매 후 이용하시기 바랍니다.

```input BFC
// BFC 수량을 결정해주세요.
let bfcAmount = 1000;
```

```input-Verify
assert(bfcAmount > 0, "잘못된 금액이 입력 되었습니다.");
assert(isCurrency (bfcAmount), "잘못된 형식의 값이 입력 되었습니다.");
assert(bfcAmount <= Q.Token.balanceOf ("bfc"), "BFC 잔액이 부족합니다.");
let ethBalance = getBalance ();
let ethAmount = Q.sushi.getETHAmountsOutFromExactIn("bfc", bfcAmount);
assert(ethAmount <= ethBalance, "ETH 잔액이 부족합니다. BFC의 수량을 낮게 조절하십시요." );
```

### Sushiswap의 BFC-WETH 풀에 유동성을 추가합니다.

- Sushiswap 기본 슬리피지 값(0.5%)을 사용합니다.

```taster
let lpAmount = Q.sushi.addLiquidityETH ("bfc", bfcAmount, ethAmount);
assert (lpAmount > 0, "유동성 토큰 잔액이 0입니다.");
```

### 이제, LP 토큰을 BiFi에 풀링하도록 하겠습니다. BiFi에 Sushiswap의 LP 토큰을 풀링하면, BiFi 토큰을 보상으로 지급합니다.

```taster
// 이제, LP 토큰을 BiFi에 풀링하겠습니다.
Q.bifi.depositLp ("bfc", lpAmount);
```

### 모든 Step이 정상적으로 완료되었습니다.

- 이제 BiFi 서비스로 이동하여, 예금 상황을 확인하세요. [바이파이 서비스로 이동](https://app.bifi.finance/pool/sushiswap/bfcEth?chainid=mainnet)
