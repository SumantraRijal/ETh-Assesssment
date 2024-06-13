CREATING A TOKEN

This Solidity contract defines a basic Ethereum token named "MyToken" with some simple functionalities.

Purpose:
The purpose of this contract is to create a token with a name, abbreviation, and total supply. It allows minting new tokens (increasing the total supply) and burning tokens (decreasing the total supply). It also keeps track of the balances of different addresses.

Components:

1. Public Variables:

string public TokenName = "John Cena";
string public TokenAbbrv = "JC";
uint public TotalSupply = 0;

TokenName: A string representing the name of the token. Here, it's set to "John Cena".

TokenAbbrv: A string representing the abbreviation of the token. Here, it's set to "JC".

TotalSupply: An unsigned integer representing the total supply of the token. It's initially set to 0.

2. Mapping Variable:
   
mapping (address => uint) public balances;

balances: A mapping that links an Ethereum address to an unsigned integer representing the balance of tokens held by that address.

4. Mint Function:

function mint(address _address, uint _value) public {
TotalSupply += _value;
balances[_address] += _value;
}
   
  The `mint` function allows us to create new tokens.
Parameters:
     - `_address`: The address to which new tokens will be assigned.
     - `_value`: The amount of tokens to be created.
     It increases the `TotalSupply` by the `_value`.
     It also increases the balance of the specified `_address` by the `_value`.

6. Burn Function:
   function burn(address _address, uint _value) public {
       if (balances[_address] >= _value) {
           TotalSupply -= _value;
           balances[_address] -= _value;
       }
   }
   
   The `burn` function allows destroying tokens, effectively decreasing the total supply.
   Parameters:
     - `_address`: The address from which tokens will be burned.
     - `_value`: The amount of tokens to be destroyed.
    It first checks if the specified `_address` has at least `_value` tokens.
    If the condition is met, it decreases the `TotalSupply` by `_value`.
    It also decreases the balance of the specified `_address` by `_value`.

 Summary:
- This contract implements a basic token with a name ("John Cena") and abbreviation ("JC").
- It maintains the total supply of the token and the balances of individual addresses.
- The `mint` function allows increasing the total supply by adding tokens to an address.
- The `burn` function allows decreasing the total supply by removing tokens from an address, provided the address has enough tokens to burn.
