# UbiquityCreditToken
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/021a1767655c717ff939fd1e4c995d537ff29f07/src/dollar/core/UbiquityCreditToken.sol)

**Inherits:**
[ERC20Ubiquity](/src/dollar/core/ERC20Ubiquity.sol/abstract.ERC20Ubiquity.md)

Credit token contract


## Functions
### constructor

Contract constructor


```solidity
constructor(address _manager) ERC20Ubiquity(_manager, "Ubiquity Credit", "uCR");
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_manager`|`address`|Access control address|


### onlyCreditMinter

Modifier checks that the method is called by a user with the "Credit minter" role


```solidity
modifier onlyCreditMinter();
```

### onlyCreditBurner

Modifier checks that the method is called by a user with the "Credit burner" role


```solidity
modifier onlyCreditBurner();
```

### raiseCapital

Raises capital in the form of Ubiquity Credit Token

*CREDIT_TOKEN_MINTER_ROLE access control role is required to call this function*


```solidity
function raiseCapital(uint256 amount) external;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`amount`|`uint256`|Amount to be minted|


### burnFrom

Burns Ubiquity Credit tokens from specified account


```solidity
function burnFrom(address account, uint256 amount) public override onlyCreditBurner whenNotPaused;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`account`|`address`|Account to burn from|
|`amount`|`uint256`|Amount to burn|


### mint

Creates `amount` new Credit tokens for `to`


```solidity
function mint(address to, uint256 amount) public override onlyCreditMinter whenNotPaused;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`to`|`address`|Account to mint Credit tokens to|
|`amount`|`uint256`|Amount of Credit tokens to mint|


