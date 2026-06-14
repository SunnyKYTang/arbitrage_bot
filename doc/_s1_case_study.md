# Case Study

Real-world blockchains are rife with arbitrage opportunities. To demonstrate the mechanics of `triangular` arbitrage, we analyze the randomly chosen transaction with hash.[0x53663b0649dd238f1e0434adec853ce405af108595155e950027e2ec9e1ba68a](https://etherscan.io/tx/0x53663b0649dd238f1e0434adec853ce405af108595155e950027e2ec9e1ba68a) firstly.

The arbitrage transaction was mined in block 22,185,681. To analyze the pre-transaction state and to identify the operational requirements for an arbitrage bot, we fork the Ethereum mainnet at the preceding block height of 22,185,680. By replicating the blockchain state at this specific block, the formation mechanism of the arbitrage opportunity can be examined, and the conditions for its detectability can be determined.
 
Within a liquidity pool, the ratio of the two token reserves represents their relative price. Consider the example below, where we derive the relative price of the token "HarryPotterObamaSonic10Inu" (denoted as BITCOIN in some contexts) using the following expression: This transaction contains two arbitrage sequences, and our discussion focuses on the first one.
In the first sequence, the arbitrator move funds across uniswap v2 and v3 pools, and eventually get profit of `0.00027410719551129725` WETH.
```commandline
>>> 0.158754775792494336 - 0.15848066859698304
0.00027410719551129725
```
Then, we identify another Uniswap V3 pool that contains Wrapped Ether (WETH) and SPX6900 (SPX). By repeating the same method used for the first pool, we query the slot0() function of the second pool at address 0x7C706586679Af2BA6D1A9fC2DA9C6aF59883fdD3:
```anvil --fork-url https://eth-mainnet.g.alchemy.com/v2/$YourAlchemyApiKey$ --fork-block-number 22185680.```

```cast call 0x0c30062368eEfB96bF3AdE1218E685306b8E89Fa "slot0()"| xargs cast --abi-decode "a()(uint160,int24,uint16,uint16,uint16,uint8,bool)"```
The output returns the following values:
```
38176274654809847206185210137346 [3.817e31]
123558 [1.235e5]
956
1000
1000
0
true
```
Step 4: Calculate SPX/WETH price using same formula:
price_SPX_WETH = (50163414224411164931748891 / 2^96)^2

Step 5: Triangular arbitrage price comparison
Cross price: Price_BITCOIN_SPX = Price_WETH_BITCOIN * Price_SPX_WETH

The arbitrage transaction was mined in block 22,185,681. It contains two
arbitrage sequences, and our discussion focuses on the first one. In this
sequence, the arbitrageur moves funds across Uniswap V2 and V3 pools,
ultimately realizing a profit of 0.00027410719551129725 WETH.

Profit calculation:
0.158754775792494336 - 0.15848066859698304 = 0.00027410719551129725 WETH
"""




By the following command, I study the state of the pools.
```bash
anvil --fork-url https://eth-mainnet.g.alchemy.com/v2/$YourAlchemyApiKey$ --fork-block-number 22185680
```