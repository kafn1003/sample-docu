---
sidebar_position: 2
---

# Settlement

*How to Calculate Cash Settlements*

## Introduction

<p style={{ fontSize: '17px', textAlign: 'justify' }}> This documentation provides an explanation of a specific functionality in a financial trading system, designed for options trading. This particularly presents details on how cash settlement amounts are calculated for options contracts. The DCL Settlement function is structured to accommodate both Call and Put options, catering to different trading strategies.</p>


## Overview
<p style={{ fontSize: '17px', textAlign: 'justify' }}>In cash settlements, the cash amount that needs to be settled in an options trade is calculated. In the calculation, the following are necessary values which are considered such as the **type of option** (Call or Put), **the side of the trade** (Buy or Sell), the **settlement price**, the **strike price**, the **contract size**, and the **currency of settlement**.</p>

<p style={{ fontSize: '17px', textAlign: 'justify' }}>
> To compute the settlement amount, there are two different ways depending on the option type.
> - **Call Option**: *(Settlement Price - Strike Price) * Contract Size*
>
> - **Put Option**: *(Strike Price - Settlement Price) * Contract Size*
</p>

## Parameters

<p style={{ fontSize: '17px', textAlign: 'justify' }}>
As mentioned, cash settlement calculation required necessary values like the option kind, side of trade, settlement price, strike price, contract size and the settlement currency. Here is the breakdown of those parameters:

1.	**Option Kind**: Type of the option, either 'Call' or 'Put'.
2.	**Side**: The side of the trade, either 'Buy' or 'Sell'.
3.	**Settlement Price**: Price of the underlying asset at settlement time.
4.	**Strike Price**: Price at which the option can be exercised.
5.	**Contract Size**: Size of the contract.
6.	**Settlement Currency**: Currency in which the settlement is made.
</p>

## Sample Scenarios
<p style={{ fontSize: '17px', textAlign: 'justify' }}>
- If a **Call** option is **bought** at a settlement price that is higher than the strike price, then the calculated settlement amount is **positive**.
- If a **Call** option is **sold** at a settlement price that is higher than the strike price, then the calculated settlement amount is **negative**.
- If a **Put** option is bought at a strike price that is higher than the settlement price, then the calculated settlement amount is **positive**.
- If a **Put** option is sold at a strike price that is higher than the settlement price, then the calculated settlement amount is **negative**.
</p>

| Settlement Price | Strike Price | Side of Trade   | Settlement Amount                                    |
|------------------|--------------|-----------------|------------------------------------------------------| 
| $3,000           | $2,400       | Buy             | Call: 600 (3,000-2,400)<br />Put: -600 (2,400-3,000) | 
| $2,500           | $1,700       | Sell            | Call: -800 (1,700-2,500)<br />Put: 800 (2,500-1,700) |

<br />

:::note
Meanwhile, the following scenarios are not accepted when calculating for the settlement amount:
- Any negative input values (e.g. -$2,300 settlement, -$5,000 strike, etc.)
- Positive contract size for Sell side (Contract size must be negative.)
- Negative contract size for Buy side (Contract size must be positive.)
:::


<!-- To demonstrate the functionality, here are sample scenarios illustrating how the function works in different cases:

| Call/Put   | Buy/Sell   | Function and Return                                  | Notation                                             |
| ---------- | ---------- | ---------------------------------------------------- | ---------------------------------------------------- |
| Call       | Buy        | Calculates positive settlement for a 'Buy' side call option. If a call option is bought at a settlement price higher than the strike price, the settlement amount is **positive**.   | *Settlement Price > Strike Price = Positive Settlement Amount*                                                     |
| Call       | Sell       | Calculates negative settlement for a 'Sell' side call option. For a sold call option with a settlement price higher than the strike price, the settlement amount is **negative**.  | *Settlement Price > Strike Price = Negative Settlement Amount*                                                     |
| Put        | Buy        | Calculates positive settlement for a 'Buy' side put option. If a put option is bought at a strike price higher than the settlement price, the settlement amount is **positive**.  |  *Strike Price > Settlement Price = Positive Settlement Amount*                                                    |
| Put        | Sell       | Calculates negative settlement for a 'Sell' side put option. For sold put option with a strike price higher than the settlement price, the settlement amount is **negative**.  | *Strike Price > Settlement Price = Negative Settlement Amount*                                                     |

Furthermore, the following samples are scenarios in which the calculation will result to an Error.

| Sample Scenario                           | Returns                                                      | Error Message                                    |
| ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------ |
| Negative Input Values                     | Returns an error for negative input values.                  | *"All input values must be positive."*           |
| Invalid Contract Size for Sell Side       | Returns an error for positive contract size on 'Sell' side.  | *"contract size must be negative for sell side"* |
| Invalid Contract Size for Buy Side        | Returns an error for negative contract size on 'Buy' side.   | *"contract size must be positive for buy side"*  | -->
