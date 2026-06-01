### Introduction
Triangular arbitrage is a commonly used trading strategy in financial and cryptocurrency markets. It refers to the process of taking advantage of price differences among three related trading pairs in order to generate profit. With the rapid development of blockchain technology and decentralized exchanges, triangular arbitrage has become an important research topic in modern digital asset trading.
In this report, a classic triangular arbitrage case is used to explain the fundamental principles behind this trading strategy. Through the analysis of this case, the mechanism of triangular arbitrage can be clearly understood, particularly how price discrepancies between different trading pairs or blockchain networks create arbitrage opportunities.
Compared with traditional arbitrage strategies, triangular arbitrage is generally more complex due to the involvement of multiple transactions and stricter timing requirements. Therefore, the establishment of an efficient triangular arbitrage system requires accurate market analysis, rapid transaction execution, and effective risk management.
This report will further discuss the operational process of triangular arbitrage in a detailed and systematic manner. In addition, the report will demonstrate how a triangular arbitrage system can be designed and implemented, as well as analyze its workflow and practical challenges. Several related concepts and supporting knowledge will also be introduced to provide a more comprehensive understanding of the topic.

Case analysis
In this technical report, you will learn about the background, the specific case of triangular arbitrage, also, you will learn how to design a triangular arbitrage step by step.
In order to study this specific case, we firstly fork the Ethereum mainnet at the block of 22185680. At that specific time period, we can therefore, figure out how the arbitrage opportunity is formed and how can we find it.
In the liquidity pool, the ratio of the numbers of the two tokens represents the relative price of that token. Look an the case below, we can figure out the relative price of HarryPotterObamaSonic10I...
(BITCOIN) using the following expression.

```anvil --fork-url https://eth-mainnet.g.alchemy.com/v2/$YourAlchemyApiKey$ --fork-block-number 22185680.```

```cast call 0x0c30062368eEfB96bF3AdE1218E685306b8E89Fa "slot0()"| xargs cast --abi-decode "a()(uint160,int24,uint16,uint16,uint16,uint8,bool)"```
```
38176274654809847206185210137346 [3.817e31]
123558 [1.235e5]
956
1000
1000
0
true
```

result token1 Wrapped Ether (WETH)/ token0 HarryPotterObamaSonic10I...(BITCOIN): 232181.66726585582
$(sqrtPriceX/96^2)^2$
Then, we find another pool with Wrapped Ether (WETH) and SPX6900 (SPX) in it. By repeating the method used in the first pool, we can also calculate the relative price of SPX6900 (SPX) in this second pool. By comparing the relative price of SPX6900 (SPX) and the quotient of the two results of the V3 pools. Therefore, we can find the price difference in the triangular arbitrage.

```cast call 0x7C706586679Af2BA6D1A9fC2DA9C6aF59883fdD3 "slot0()" | xargs cast --abi-decode "a()(uint160,int24,uint16,uint16,uint16,uint8,bool)"```
```
50163414224411164931748891 [5.016e25]
-147304 [-1.473e5]
963
1800
1800
0
true
```

the first value comeout by$sqrtPriceX96= \sqrt{\frac{token1}{token0}}×2^{96}$ 
token0 Wrapped Ether (WETH) token1 SPX6900 (SPX)
token1 Wrapped Ether (WETH)/ token0 HarryPotterObamaSonic10I...(BITCOIN)*token1 SPX6900 (SPX)/token0 Wrapped Ether (WETH)

As the triangular arbitrage is designed with two V3 pools and one V2 pool, we need to find a V2 pool containing mainly SPX6900 (SPX) and HarryPotterObamaSonic10I...
(BITCOIN), the Wrapped Ether (WETH) in the two V3 pools is to connect the value of the SPX6900 (SPX) and HarryPotterObamaSonic10I...
(BITCOIN) together. By using the equation below, we can calculate the relative price of HarryPotterObamaSonic10I...
(BITCOIN) in the V2 pool. 
V2 token0 hp 
```cast call 0x72e4f9F808C49A2a61dE9C5896298920Dc4EEEa9 \                                                     
"balanceOf(address)(uint256)" \
0x7c1C4a2Cf81D2fC83b89bfD34F4d2c7e90044b32
517982348923589 [5.179e14]
```
token1 SPX
```cast call 0xE0f63A424a4439cBE457D80E4f4b51aD25b2c56C \
"balanceOf(address)(uint256)" \
0x7c1C4a2Cf81D2fC83b89bfD34F4d2c7e90044b32
47280536047575 [4.728e13]
```

$sqrtPriceX96= \sqrt{\frac{token1}{token0}}×2^{96}$