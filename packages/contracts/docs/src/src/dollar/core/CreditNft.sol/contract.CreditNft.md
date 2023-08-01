# CreditNft
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/021a1767655c717ff939fd1e4c995d537ff29f07/src/dollar/core/CreditNft.sol)

**Inherits:**
[ERC1155Ubiquity](/src/dollar/core/ERC1155Ubiquity.sol/contract.ERC1155Ubiquity.md), [ICreditNft](/src/dollar/interfaces/ICreditNft.sol/interface.ICreditNft.md)

CreditNft redeemable for Dollars with an expiry block number

ERC1155 where the token ID is the expiry block number

*Implements ERC1155 so receiving contracts must implement `IERC1155Receiver`*

*1 Credit NFT = 1 whole Ubiquity Dollar, not 1 wei*


## State Variables
### _totalOutstandingDebt
Total amount of CreditNfts minted

*Not public as if called externally can give inaccurate value, see method*


```solidity
uint256 private _totalOutstandingDebt;
```


### _tokenSupplies
Mapping of block number and amount of CreditNfts to expire on that block number


```solidity
mapping(uint256 => uint256) private _tokenSupplies;
```


### _sortedBlockNumbers
Ordered list of CreditNft expiries


```solidity
StructuredLinkedList.List private _sortedBlockNumbers;
```


## Functions
### onlyCreditNftManager

Modifier checks that the method is called by a user with the "CreditNft manager" role


```solidity
modifier onlyCreditNftManager();
```

### constructor

Contract constructor

*URI param is if we want to add an off-chain meta data uri associated with this contract*


```solidity
constructor(address _manager) ERC1155Ubiquity(_manager, "URI");
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`_manager`|`address`|Access control address|


### mintCreditNft

Mint an `amount` of CreditNfts expiring at `expiryBlockNumber` for a certain `recipient`


```solidity
function mintCreditNft(address recipient, uint256 amount, uint256 expiryBlockNumber) public onlyCreditNftManager;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`recipient`|`address`|Address where to mint tokens|
|`amount`|`uint256`|Amount of tokens to mint|
|`expiryBlockNumber`|`uint256`|Expiration block number of the CreditNFTs to mint|


### burnCreditNft

Burns an `amount` of CreditNfts expiring at `expiryBlockNumber` from `creditNftOwner` balance


```solidity
function burnCreditNft(address creditNftOwner, uint256 amount, uint256 expiryBlockNumber) public onlyCreditNftManager;
```
**Parameters**

|Name|Type|Description|
|----|----|-----------|
|`creditNftOwner`|`address`|Owner of those CreditNFTs|
|`amount`|`uint256`|Amount of tokens to burn|
|`expiryBlockNumber`|`uint256`|Expiration block number of the CreditNFTs to burn|


### updateTotalDebt

Updates debt according to current block number

Invalidates expired CreditNfts

*Should be called prior to any state changing functions*


```solidity
function updateTotalDebt() public;
```

### getTotalOutstandingDebt

Returns outstanding debt by fetching current tally and removing any expired debt


```solidity
function getTotalOutstandingDebt() public view returns (uint256);
```

## Events
### MintedCreditNft
Emitted on CreditNfts mint


```solidity
event MintedCreditNft(address recipient, uint256 expiryBlock, uint256 amount);
```

### BurnedCreditNft
Emitted on CreditNfts burn


```solidity
event BurnedCreditNft(address creditNftHolder, uint256 expiryBlock, uint256 amount);
```

