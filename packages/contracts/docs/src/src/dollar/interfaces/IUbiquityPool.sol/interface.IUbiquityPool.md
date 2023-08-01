# IUbiquityPool
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/be04500228f975a0d77b1f17e5465c27c035525b/src/dollar/interfaces/IUbiquityPool.sol)

Ubiquity pool interface

Allows users to:
- deposit collateral in exchange for Ubiquity Dollars
- redeem Ubiquity Dollars in exchange for the earlier provided collateral


## Functions
### mintDollar

Mints 1 Ubiquity Dollar for every 1 USD of `collateralAddress` token deposited


```solidity
function mintDollar(address collateralAddress, uint256 collateralAmount, uint256 dollarOutMin) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`collateralAddress`|`address`|address of collateral token being deposited|
|`collateralAmount`|`uint256`|amount of collateral tokens being deposited|
|`dollarOutMin`|`uint256`|minimum amount of Ubiquity Dollars that'll be minted, used to set acceptable slippage|


### redeemDollar

Burns redeemable Ubiquity Dollars and sends back 1 USD of collateral token for every 1 Ubiquity Dollar burned

*Redeem process is split in two steps:*

*1. `redeemDollar()`*

*2. `collectRedemption()`*

*This is done in order to prevent someone using a flash loan of a collateral token to mint, redeem, and collect in a single transaction/block*


```solidity
function redeemDollar(address collateralAddress, uint256 dollarAmount, uint256 collateralOutMin) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`collateralAddress`|`address`|address of collateral token being withdrawn|
|`dollarAmount`|`uint256`|amount of Ubiquity Dollars being burned|
|`collateralOutMin`|`uint256`|minimum amount of collateral tokens that'll be withdrawn, used to set acceptable slippage|


### collectRedemption

Used to collect collateral tokens after redeeming/burning Ubiquity Dollars

*Redeem process is split in two steps:*

*1. `redeemDollar()`*

*2. `collectRedemption()`*

*This is done in order to prevent someone using a flash loan of a collateral token to mint, redeem, and collect in a single transaction/block*


```solidity
function collectRedemption(address collateralAddress) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`collateralAddress`|`address`|address of the collateral token being collected|


### addToken

Admin function for whitelisting a token as collateral


```solidity
function addToken(address collateralAddress, IMetaPool collateralMetaPool) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`collateralAddress`|`address`|Address of the token being whitelisted|
|`collateralMetaPool`|`IMetaPool`|3CRV Metapool for the token being whitelisted|


### setRedeemActive

Admin function to pause and unpause redemption for a specific collateral token


```solidity
function setRedeemActive(address collateralAddress, bool notRedeemPaused) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`collateralAddress`|`address`|Address of the token being affected|
|`notRedeemPaused`|`bool`|True to turn on redemption for token, false to pause redemption of token|


### getRedeemActive

Checks whether redeem is enabled for the `_collateralAddress` token


```solidity
function getRedeemActive(address _collateralAddress) external view returns (bool);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_collateralAddress`|`address`|Token address to check|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`bool`|Whether redeem is enabled for the `_collateralAddress` token|


### setMintActive

Admin function to pause and unpause minting for a specific collateral token


```solidity
function setMintActive(address collateralAddress, bool notMintPaused) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`collateralAddress`|`address`|Address of the token being affected|
|`notMintPaused`|`bool`|True to turn on minting for token, false to pause minting for token|


### getMintActive

Checks whether mint is enabled for the `_collateralAddress` token


```solidity
function getMintActive(address _collateralAddress) external view returns (bool);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_collateralAddress`|`address`|Token address to check|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`bool`|Whether mint is enabled for the `_collateralAddress` token|


### getRedeemCollateralBalances

Returns the amount of collateral ready for collecting after redeeming

*Redeem process is split in two steps:*

*1. `redeemDollar()`*

*2. `collectRedemption()`*

*This is done in order to prevent someone using a flash loan of a collateral token to mint, redeem, and collect in a single transaction/block*


```solidity
function getRedeemCollateralBalances(address account, address collateralAddress) external view returns (uint256);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`account`|`address`|Account address for which to check the balance ready to be collected|
|`collateralAddress`|`address`|Collateral token address|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`uint256`|Collateral token balance ready to be collected after redeeming|


