# Introduction


A variety of financial instruments, including `arbitrage`, `liquidation`, `lending`, etc. have been migrated to the cryptocurrency space and are now implemented within the crypto ecosystem.

By utilizing these tools, individuals can lunch large-scale financial activities independently, without requiring privileged access or additional external resources.

![No priviledge in crypto world](img/homepage_illustration.webp "It was the best of times, it was the worst of times")

Among these instruments, arbitrage bots generate profit by exploiting price discrepancies across different chains, DEXs, or liquidity pools.
In this technical report, I will guide you step by step on designing an arbitrage bot, covering `cross-chain`, `cross-DEX`, and `triangular arbitrage` in the era of cryptocurrency.

Before getting started, I recommend that readers consult the following materials for a better understanding of this report:

```commandline
https://uniswapv3book.com/index.html
https://app.uniswap.org/whitepaper.pdf
https://app.uniswap.org/whitepaper-v3.pdf
https://developers.uniswap.org/docs
```

The tools I used include:
```commandline
[Foundry](https://github.com/foundry-rs/foundry)
```
<span style="color:red"><b>Disclaimer: This code is for educational purposes only and comes with no guarantee of profit or performance.</b></span>