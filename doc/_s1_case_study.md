# Case Study

Real-world blockchains are rife with arbitrage opportunities. To demonstrate the mechanics of `triangular` arbitrage, we analyze the randomly chosen transaction with hash.[0x53663b0649dd238f1e0434adec853ce405af108595155e950027e2ec9e1ba68a](https://etherscan.io/tx/0x53663b0649dd238f1e0434adec853ce405af108595155e950027e2ec9e1ba68a) firstly.

The arbitrage transaction was mined in block 22,185,681. To analyze the pre-transaction state and to identify the operational requirements for an arbitrage bot, we fork the Ethereum mainnet at the preceding block height of 22,185,680. By replicating the blockchain state at this specific block, the formation mechanism of the arbitrage opportunity can be examined, and the conditions for its detectability can be determined.
 
Within a liquidity pool, the ratio of the two token reserves represents their relative price. Consider the example below, where we derive the relative price of the token "HarryPotterObamaSonic10Inu" (denoted as BITCOIN in some contexts) using the following expression: This transaction contains two arbitrage sequences, and our discussion focuses on the first one.
In the first sequence, the arbitrator move funds across uniswap v2 and v3 pools, and eventually get profit of `0.00027410719551129725` WETH.
```commandline
>>> 0.158754775792494336 - 0.15848066859698304
0.00027410719551129725
```
The related tokens and pools of this sequence are:



By the following command, I study the state of the pools.
```bash
anvil --fork-url https://eth-mainnet.g.alchemy.com/v2/$YourAlchemyApiKey$ --fork-block-number 22185680
```