Download Link: https://assignmentchef.com/product/solved-blockchain-foundation-blockchain-practical-hw3
<br>
<h1>Problem 1 – Hello World</h1>

Let’s say Hello to the world of ethereum smart contracts. In this section, you will write a smart contract which its sole purpose is to greet people. Create a file in remix, paste Greeter.sol in it and Deploy the contract using ”Hello From #YOUR STUDENT NUMBER” as argument (replace #YOUR STUDENT NUMBER with your student number).

<strong>Deliverable: </strong>Call greeting method and place a screenshot of the result in your report.

<h1>Problem 2 – Getting Familiar with ERC20 Token</h1>

In this section you are going to implement a custom version of ERC20 token. First of all, What is an ERC20 token?

ERC20, which stands for Ethereum Requests for Comment, is a set of programming rules that all Ethereum-based tokens are expected to follow. The Ethereum Developers agreed on these three (optional) variables, six functions, and two logging events as protocol standard for the minimal viable token, in order to normalize expected behaviors while communicating across the Ethereum network. By establishing this protocol, Ethereum developers are able to more easily integrate and work with token contracts already published to the network.[1]

interface CustomERC20 { function totalSupply() external view returns (uint256); function balanceOf(address account) external view returns (uint256); function transfer(address recipient, uint256 amount) external returns (bool); function allowance(address owner, address spender) external view returns (uint256); function approve(address spender, uint256 amount, uint expireTime) external returns (bool); function transferFrom(address sender, address recipient, uint256 amount) external returns (bool);

function pause() public returns (bool); event Transfer(address indexed from, address indexed to, uint256 value); event Approval(address indexed owner, address indexed spender, uint256 value); event TimeApproval(address owner, address spender, uint256 expireTime); event Paused(address account); event Unpaused(address account);

}

<ul>

 <li>Approve: same as ECR20 approve with one exrta argument. Expire time is the duration (in seconds) that token owner gives allowance to spender.</li>

 <li>Pause: Pauses contract all external and public functions.</li>

</ul>

Complete CutomERC20.sol in order to satisfy requirements.

<strong>Deliverable: </strong>CutomERC20.sol

<h1>Problem 3 – eBook Library</h1>

The manager of an eBook library has decided to lend his books through Ethereum smart contract to show that he follows the latest technology. He wants this smart contract to support the following functionality:

<ul>

 <li>The eBook library doesn’t accept Ethereum and has its own token named “ELT” . all users need to exchange their Ether for ELT in order to use the library services.</li>

 <li>The admin can add books to the smart contract.</li>

 <li>A book is accessible by 1 user at the same time and until the access of the last user to the book hasn’t been revoked, no one else can access this book even though he/she pay for the book.</li>

 <li>All the books are determined by a unique ID. The contract keeps a list of all books and their specifications including their validity (means that if this bookId has been added by admin before), their genre and their access fee. All the prices are in ELT.</li>

 <li>Any user that wants to access a book, should call “access” function and determine the Id of the book he/she wants to access and pay the access fee of that book. If the Id is valid and the book is available (not in access by someone else) access to this book will be granted to the user for an “accessDuration”.</li>

 <li>The smart contract keeps a mapping of all rented books to the information of the user which has access to them and the “accessStartTime” and if the book is available or not.</li>

 <li>The “accessDuration” is defined by the admin, and after this passes the admin can revoke the user’s access to the book.</li>

 <li>A user can call “changeToPremium” function and pay “premiumFee” in SLTs and become a premium user.</li>

 <li>“premiumFee” is determined by admin in the constructor.</li>

 <li>Premium users have a special privilege. if they want access to a book that is rented by a regular user, the access of that regular user to that book is revoked and the access fee is transferred to his/her ELT account and the access of the book is granted to the premium user. But if the current renter also has a premium account, the new user can’t access the book. In other words, premium users have a priority over regular users but they don’t have any priority over other premium users. notice that premium users also should pay for any book they rent like regular users.</li>

 <li>“EBookLibrary” contract is a child of the “CustomERC20” contract which you completed in problem 2. Inheritance in solidity study this tutorial. https://www.tutorialspoint.com/solidity/solidity inheritance.htm</li>

 <li>There is a function “deposit” in the “EBookLibrary” contract which accepts Ether and allocates the sender the same amount of ELTs.</li>

 <li>Any user who wants to exit the library, can call the “withdraw” function and withdraw his/her unspent ELTs in Ether.</li>

</ul>

<strong>Example scenario:</strong>

<ol>

 <li>Sara creates the smart contract by this input: (“600”,“EBookLibraryToken” , “ELT”,“18”,“10”)</li>

 <li>Sara adds book (“1”, “1”, “4”) as admin.</li>

 <li>Ali deposits 4 ELTs and then access the book “1”.</li>

 <li>Mohammad deposits 20 ELTs and then change his account to premium.</li>

 <li>Mohammad wants to access the book “1”. The access duration for Ali hasn’t ended but because Mohammad is a premium user he can access this book and Ali’s ELTs are refunded to him.</li>

</ol>

Complete EBookLibrary.sol to satisfy the properties above. Use “require” or “modifier” to ensure that a transaction reverts in case of wrong executions.

<strong>Deliverable: </strong>EBookLibrary.sol

<h1>Problem 4 – Deploy to a testnet</h1>

In this section, we are going to deploy the EBookLibrary app to Reposten public testnet.

<strong>Prerequisites:</strong>

<ul>

 <li>Download MetaMask extension from <a href="https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en">Chrome Web Store</a><a href="https://chrome.google.com/webstore/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en">.</a></li>

 <li>Go through MetaMask setup steps</li>

 <li>After setup select Ropsten Test Network from the drop down on top of the extension.</li>

 <li>Click on deposit and then GET ETHER to get your first test net ethers.</li>

 <li>in remix change the environment to Injected Web3.</li>

 <li>if everything goes right you should be able to see your account and its balance.</li>

</ul>

<strong>Deploy the contract to Ropsten network:</strong>

<ul>

 <li>Deploy the EBookLibrary to Ropsten Network using remix.</li>

 <li>MetaMask catches your request and asks you to confirm it. You can tweak some variable here too.</li>

</ul>

If everything goes right, after the confirmation your contract will be deployed to Ropsten and you can trace your transaction on <a href="https://ropsten.etherscan.io/">Etherscan</a> using the links provided in remix as well as MetaMask. Make two more transaction as the admin adds books (“1”,“0”,“3”) and (“2”,“2”,“10”)

<strong>Deliverable: </strong>Stipulate the address of your contract and the hash of your transactions in your report.

<h1>Problem 5 – Let’s Do Some Hacking</h1>

<h2>Part 1</h2>

You are provided with the code for a voting voting smart contract. This smart contract suffers from a security hole which can cause it to show wrong number of votes for a candidate in certain conditions. (Hint: there is no restriction on the number of users who can vote)

<strong>Deliverable: </strong>A description of the security hole and a proposed solution to prevent it in your report (no coding).

<h2>Part 2</h2>

“withdraw” function of ”EBookLibrary” contract is vulnerable to an attack, and an attacker can drain out the balance stored in the contract. Exploit it and then change this function to fix it.

<strong>Deliverable: </strong>EBookLibrary.sol, and an explanation about the attack and your solution in your report.

<h1>Problem 6 – Example Dapp</h1>

In DApp folder you can find an application which connects a user interface to blockchain using ethereum’s web3.js library. In order to test our DApp we are going to use a blockchain emulator called Ganache. <strong>Prerequisites:</strong>

<ul>

 <li>Download Ganache from <a href="https://truffleframework.com/ganache">here</a> and start it.</li>

 <li>In remix change the environment to Web3 Provider and accept the default endpoint (if you can’t connect to the default endpoint try http://localhost:7545).</li>

 <li>If everything goes right you should be able to see ten accounts with balance 100 in the balance drop-down in remix.</li>

</ul>

<strong>Deploy the contract to Ganache:</strong>

<ul>

 <li>Deploy the voting contract (given in problem 4) to Ganache using remix.</li>

</ul>

<strong>Connect the DApp to your contract:</strong>

<ul>

 <li>Open DAPP/js/index.js</li>

 <li>Copy the contract address and paste it in the contractAddress field (line 12).</li>

 <li>Copy the contract ABI and past it in the abi field (line 16). You can copy it from “SOLIDITY COMPILER” tab in remix.</li>

 <li>Make sure web3 provider port is correct (line 9),</li>

 <li>Open voting.html</li>

</ul>

You should be able to see a working voting DApp.

<strong>Deliverable: </strong>vote to the candidates several times using the DApp UI and place a screenshot of the DApp (after your votes) in your report.

<h2>References</h2>

[1] Advanced Cryptocurrency Topics: ERC20 Interface https://medium.com/setocean/advanced-cryptocurrency-topics-erc20-interface-7372e97f4a42