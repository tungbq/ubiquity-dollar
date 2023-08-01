# LibCreditNftRedemptionCalculator
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/021a1767655c717ff939fd1e4c995d537ff29f07/src/dollar/libraries/LibCreditNftRedemptionCalculator.sol)

Library for calculating amount of Credit NFTs to mint on Dollars burn


## Functions
### getCreditNFTAmount

Returns Credit NFT amount minted for `dollarsToBurn` amount of Dollars to burn


```solidity
function getCreditNFTAmount(uint256 dollarsToBurn) internal view returns (uint256);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`dollarsToBurn`|`uint256`|Amount of Dollars to burn|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`uint256`|Amount of Credit NFTs to mint|


