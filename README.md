#### estimateGas() Contract Deployment Error Explained
---

When deploying contracts on-chain using a Provider like infura or alchemy. Your transaction may fail with: 

![image](https://user-images.githubusercontent.com/90874464/179557037-96450617-5587-4e8e-9afa-68ae4ea02390.png)

I as well as others experienced this issue when testing queryWinner and delegateVoter scripts during Lesson 4 Weekend homework. 

It turns out this is not an issue with ethers.js or the smart contract code in itself. It stems from the `Provider` itself which is the gateway that interacts with the ethereum network.  

This can be a legitimate issue with gas(although I have not hit it) *or* an issue with the contract addresses not having the correct permissions to interact with the contract. 

Unfortunately, there's no way to tell from the error itself where the problem in the contract is but based on the context of the contract you are trying to interact with you can begin to debug by tracing from said contract e.g. If you were trying to `delegate` voting rights from the `chairperson address` to another voter address. Did that `voter address` already recieve voter permissions from the `chairperson` address? Did that voter address you're trying to delegate to already vote? 
