# MockERC20
[Git Source](https://github.com/tungbq/ubiquity-dollar/blob/021a1767655c717ff939fd1e4c995d537ff29f07/src/dollar/mocks/MockERC20.sol)

**Inherits:**
ERC20


## Functions
### constructor


```solidity
constructor(string memory _name, string memory _symbol, uint8 _decimals) ERC20(_name, _symbol);
```

### mint


```solidity
function mint(address to, uint256 value) public virtual;
```

### burn


```solidity
function burn(address from, uint256 value) public virtual;
```

