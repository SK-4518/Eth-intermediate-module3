# Eth-intermediate-module3
**Aim of the Project**

Write a smart contract to create your own token on a local HardHat network and use Remix ide to interact with it.

**Code of the project**

      //SPDX-License-Identifier: UNLICENSED
      
      pragma solidity ^0.8.9;
      
      import "hardhat/console.sol";
   
     contract Token {
     
    string public tokenName = "Custom Hardhat Token";
    string public tokenAbbreviation = "CHT";
    uint256 public totalSupply = 1000000;
    address public owner;

    mapping(address => uint256) balances;
    
    event Transfer(address indexed _from, address indexed _to, uint256 _value);

    constructor() {
        balances[msg.sender] = totalSupply;
        owner = msg.sender;
    }

    function transferToken(address to, uint256 amount) external {
       
        require(balances[msg.sender] >= amount, "Not enough tokens");
        console.log(
            "Transferring from %s to %s %s tokens",
            msg.sender,
            to,
            amount
        );
        
        balances[msg.sender] -= amount;
        balances[to] += amount;

        emit Transfer(msg.sender, to, amount);
    }

  
    function balanceOf(address account) external view returns (uint256) {
        return balances[account];
    }
    
    }

**Codes Logic**

1. Mention the License Identifier and solidity compiler version.

2. Import the hardhat library to use the console.log feature of the hardhat network.

3. Create a contract Token. The variable tokenName and tokenAbbreviation will help us to identify the details of our token.

4. totalSupply will be the fixed amount of tokens that are stored in an unsigned integer.

5. owner variable will be of address type which will be used to store the accounts.

6. mapping is used to store the balance of the accounts.

7. Event transfer will supervise the transfer specified amount of tokens from the sender address to the receiver address.

8. In the constructor, we assign the totalSupply to the balance of the sender. Also, we initialize the msg.sender to be the owner.

9. The function transferToken takes the receiver address and the amount of token to be transferred as its parameters. It is declared as external which means it is callable outside of the contract as well.

10. Inside the function we use the require statement checks that the balance of the owner should be greater than or equal to the amount which needs to be transferred. If this condition returns to true then we print the message using the console.log that we are transferring the tokens.

11. Also we deduct the amount from the balance of the sender and add that same amount to the balance of the receiver address.

12. Then emit from the Transfer event.

13. At last, the function balanceOfAccount returns the balance of the account after the transfer of the tokens.


**Steps to follow to check the code's functionality**

1. Open the vs code terminal. Type 'npm install' to download the project dependencies.

2. Then type 'npm install -g @remix-project/remixd' in order to install the remixd globally on our pc.

3. Then type 'remixd -s ./ --remix-ide https://remix.ethereum.org' in order to connect our hardhat project with the remix ide.

4. Type 'npx hardhat node' which will give us a list of accounts and private keys to be used in our hardhat local network. Also, it will give us the server at which our smart contract is running.

5. Open the Remix ide. Click on the code sample. Then click on 'connect to localhost'. Then click on 'connect'. This will help us to load the hardhat project in the remix ide.

6. Open the contract Token.sol. Compile and deploy it.

7. After deploying it, enter the address and amount in the transfer function. Enter the address of the owner. Click on transfer. The message 'Transfering .....to..... ......tokens.' will be displayed in the console window.


**Author**
Sehajpreet Kaur 

(21BCS4518@cuchd.in)
