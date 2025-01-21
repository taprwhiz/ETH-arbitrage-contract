# **Eth-Arbitrage 2.0: Profit from Price Differences with ETH/LUSD**

**Eth-Arbitrage 2.0** is an automated system designed to exploit price discrepancies between the **ETH/LUSD** pair on **Uniswap** and **Liquity**. By executing strategic trades between these platforms, the system ensures that profits are maximized while minimizing the risks and impact of large trades.


## **How It Works**

The system operates in two simple steps:
1. **Swap ETH for LUSD** on Uniswap.
2. **Redeem LUSD for ETH** on Liquity.

These steps are executed automatically when an arbitrage opportunity arises, which happens when there's a price difference between the two platforms.


## **Project Components**

- **Node Server**: Tracks ETH prices on Chainlink and Uniswap. When a potential arbitrage opportunity is identified, it triggers the smart contract.
- **Smart Contract**: Executes the arbitrage strategy between Uniswap and Liquity.


## **How ETH Amount for Arbitrage is Calculated**

To ensure minimal market impact, the system takes into account:
1. **ETH in the wallet**.
2. **The amount of LUSD that can be redeemed on Liquity**.
3. **The reserve pool of the ETH/LUSD pair on Uniswap**.

The bot calculates the amount of ETH to use in the arbitrage using the formula:
```solidity
min( <ETH in Wallet>, <12.5% of Uniswap Pool> )
```

This keeps trades small and ensures better prices. 



## **Identifying Arbitrage Opportunities**

The bot checks for profitability using the formula:
```solidity
profit = ETH_USED * (uniswapPrice/chainLinkPrice) * (1-redemptionFee) * (1-uniswap_fee) - GasCost
```
If the profit is positive, the system triggers the trade. 

---

## **24/7 Server Operation**

To ensure the system runs continuously, it uses a **poller mechanism** that subscribes to Ethereum's new block headers. This guarantees that prices are constantly monitored and the bot is always ready to act.


Once started, the server will begin polling prices automatically. Make sure to have enough LUSD in your wallet to execute the arbitrage.

## **Deployed Contract**

Check out the contract on the **Goerli Testnet**:
![image](https://user-images.githubusercontent.com/15603274/233756332-55b737ab-4fd2-484a-88c7-99b0538de61c.png)


## **Contact Me**

- **Email**: [sakelejames@gmail.com](mailto:sakelejames@gmail.com)
- **Telegram**: [@snipmaxi](https://t.me/snipmaxi)
