# ETH_ASSESMENT

This Solidity program is a simple token minting and burning program that facilitates a demo overview of the respective real life functions.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract has 2 functions , one for minting that takes in two parameters (address and value) and another function named burn whose working is just the opposite of mint function. This particular function has certain validation conditions in it to make sure no Invalid Transaction is taking place.
## Getting Started

### Executing program

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., Token.sol). Copy and paste the following code into the file:

```javascript
// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

/*
       REQUIREMENTS
    1. Your contract will have public variables that store the details about your coin (Token Name, Token Abbrv., Total Supply)
    2. Your contract will have a mapping of addresses to balances (address => uint)
    3. You will have a mint function that takes two parameters: an address and a value. 
       The function then increases the total supply by that number and increases the balance 
       of the “sender” address by that amount
    4. Your contract will have a burn function, which works the opposite of the mint function, as it will destroy tokens. 
       It will take an address and value just like the mint functions. It will then deduct the value from the total supply 
       and from the balance of the “sender”.
    5. Lastly, your burn function should have conditionals to make sure the balance of "sender" is greater than or equal 
       to the amount that is supposed to be burned.
*/

contract Token {

    // public variables here
    string public tokenName="META";
    string public tokenAbbrv="MTA";
    uint public totalSupply=0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address,uint _value) public
    {
        totalSupply+=_value;
        balances[_address]+=_value;
        
    }

    // burn function
    function burn(address _address,uint _value) public
    {
      require(_address != address(0), "Cannot burn from the zero address");
      require(balances[_address] >= _value, "Insufficient balance to burn");
      
        totalSupply-=_value;
        balances[_address]-=_value;
        
    }
}

```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile Token.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Token" contract from the dropdown menu, and then click on the "Deploy" button. After that we have to enter the value of both the parameters, for address we can take any valid address but for the sake of this project we can just use the default address of our account given to us in Remix IDE.

Once the contract is deployed, you can interact with it by calling the mint and passing the values to mint tokens whereas call the burn function and pass the values if we want to burn the tokens.

## Authors

Yukta 
[@Chandigarh University](https://www.linkedin.com/in/yukta-/)


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
