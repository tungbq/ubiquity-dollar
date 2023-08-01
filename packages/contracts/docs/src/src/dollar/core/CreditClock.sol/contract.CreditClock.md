# CreditClock
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/021a1767655c717ff939fd1e4c995d537ff29f07/src/dollar/core/CreditClock.sol)

CreditClock contract


## State Variables
### accessCtrl
Access control contract


```solidity
IAccessControl public accessCtrl;
```


### one
ABDKMathQuad with value of 1.


```solidity
bytes16 private immutable one = uint256(1).fromUInt();
```


### rateStartBlock
The block height from where we start applying the rate.


```solidity
uint256 public rateStartBlock;
```


### rateStartValue
This is the exchange rate of Credits for the start block.


```solidity
bytes16 public rateStartValue;
```


### ratePerBlock
Deprecation rate. How many Dollars are deprecated on each block.


```solidity
bytes16 public ratePerBlock;
```


## Functions
### onlyAdmin

Modifier checks that the method is called by a user with the "Incentive manager" role


```solidity
modifier onlyAdmin();
```

### constructor

Contract constructor


```solidity
constructor(address _manager, bytes16 _rateStartValue, bytes16 _ratePerBlock);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_manager`|`address`|The address of the `_manager` contract for access control|
|`_rateStartValue`|`bytes16`|ABDKMathQuad Initial rate|
|`_ratePerBlock`|`bytes16`|ABDKMathQuad Initial rate change per block|


### setManager

Updates the manager address


```solidity
function setManager(address _manager) external onlyAdmin;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_manager`|`address`|New manager address|


### getManager

Returns the manager address


```solidity
function getManager() external view returns (address);
```
**Returns**

|Name|Type|Description|
|----|----|-----------|
|`<none>`|`address`|Manager address|


### setRatePerBlock

Sets rate to apply from this block onward


```solidity
function setRatePerBlock(bytes16 _ratePerBlock) external onlyAdmin;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_ratePerBlock`|`bytes16`|ABDKMathQuad new rate per block to apply from this block onward|


### getRate

Calculates `rateStartValue * (1 / ((1 + ratePerBlock)^blockNumber - rateStartBlock)))`


```solidity
function getRate(uint256 blockNumber) public view returns (bytes16 rate);
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`blockNumber`|`uint256`|Block number to get the rate for. 0 for current block.|

**Returns**

|Name|Type|Description|
|----|----|-----------|
|`rate`|`bytes16`|ABDKMathQuad rate calculated for the block number|


## Events
### SetRatePerBlock
Emitted when depreciation rate per block is updated


```solidity
event SetRatePerBlock(uint256 rateStartBlock, bytes16 rateStartValue, bytes16 ratePerBlock);
```

