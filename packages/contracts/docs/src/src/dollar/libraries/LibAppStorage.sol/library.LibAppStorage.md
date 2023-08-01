# LibAppStorage
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/021a1767655c717ff939fd1e4c995d537ff29f07/src/dollar/libraries/LibAppStorage.sol)

Library used as a shared storage among all protocol libraries


## Functions
### appStorage

Returns `AppStorage` struct used as a shared storage among all libraries


```solidity
function appStorage() internal pure returns (AppStorage storage ds);
```
**Returns**

|Name|Type|Description|
|----|----|-----------|
|`ds`|`AppStorage`|`AppStorage` struct used as a shared storage|


