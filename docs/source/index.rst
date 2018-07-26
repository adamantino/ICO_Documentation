
INFINITY TRADE COIN ICO Documentation
=====================================


Tools for writing and deploying smart contracts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
`Infura <https://infura.io>`_ – scalable blockchain infrastructure. Don't run a full Ethereum node, let them handle the infrastructure layer

`Mist Browser <https://github.com/ethereum/mist>`_ – browse the dApp. Separate browser to browse dApps and interact with them.

`Truffle Framework <https://truffleframework.com>`_ – The Ethereum Development framework. It has built-in smart contract compilation, linking, deployment, and binary management.

`Metamask <https://metamask.io>`_ – It allows to run Ethereum dApps right in the browser without running a full Ethereum node. It is a browser plugin that allows users to make Ethereum transactions through regular websites. 

`Remix <https://remix.ethereum.org/#optimize=false&version=soljson-v0.4.24+commit.e67f0147.js>`_ – Web IDE to write, deploy and run Solidity smart contracts

`ETHFiddle <https://ethfiddle.com/#/>`_  - Share you Solidity Script



External Documentation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
`Solidity Documentation <http://solidity.readthedocs.io/en/develop/introduction-to-smart-contracts.html>`_ - Solidity Documentation

`Create your own crypto <https://www.ethereum.org/token>`_ - Create your own crypto (official)

`ICO Smart Contact Framework <https://ico.readthedocs.io/en/latest/?badge=latest>`_ - ICO Smart Contact Framework


Smart Contract Example
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^


.. code-block:: javascript
   :linenos:

	pragma solidity ^0.4.0;
	 
	contract Coin {
	 // The keyword "public" makes those variables
	 // readable from outside.
	 address public minter;
	 mapping (address =&amp;amp;gt; uint) public balances;
	 
	 // Events allow light clients to react on
	 // changes efficiently.
	 event Sent(address from, address to, uint amount);
	 
	 // This is the constructor whose code is
	 // run only when the contract is created.
	 function Coin() {
	 minter = msg.sender;
	 }
	 
	 function mint(address receiver, uint amount) {
	 if (msg.sender != minter) return;
	 balances[receiver] += amount;
	 }
	 
	 function send(address receiver, uint amount) {
	 if (balances[msg.sender] &amp;amp;lt; amount) return;
	 balances[msg.sender] -= amount;
	 balances[receiver] += amount;
	 Sent(msg.sender, receiver, amount);
	 }
	}



.. code-block:: javascript

	address public minter;

It's a 160 bit variable ideal for storing addresses on the Ethereum network.




.. code-block:: javascript

	mapping (address =&amp;amp;amp;gt; uint) public balances;

Creates a mapping between address and unit type which stores the coin balance in each address




.. code-block:: javascript

	function Coin() {
	minter = msg.sender;
	}

Constructor function. Executed as soon as the contract is deployed. This sets the value of minter to the address which has deployed the contract. This ensures that only the owner of the contract can mint new coins and nobody else. This is ensured by the following function:



.. code-block:: javascript

	function mint(address receiver, uint amount)

Function sending coin value equal to amount to the receiver address.


.. code-block:: javascript

	function send(address receiver, uint amount)

Function sending coins to the receiver’s address from the sender's address






Deploying smart contract in Ethereum blockchain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Testnets simulate the Ethereum network and EVM. It enables developers to upload and interact with smart contracts without paying the cost of gas.

Smart contracts must pay gas for their computations on the Ethereum network. However, testnets provide environments for developers to test their contracts without paying any money. Testnet gas is available for free from many public areas. es. `ropsten <http://faucet.ropsten.be:3001>`_ 




Guide
==================
.. toctree::
   :maxdepth: 1
 
   Solidity
   scuffold
   Test Net


