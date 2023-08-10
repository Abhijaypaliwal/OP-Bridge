# OP-Bridge

The bridge.HTML contains brige to transfer assets from L1 to L2. Note that transfer could happen only with Goerli and OP-Goerli. 

1. For bridging ETH, BridgeETH function of L1StandardBridge is used. it uses an gimple contract call with parameters. Here reciever would be msg.sender
2. For bridging existing ERC20 Assets, BridgeERC20 function of same contract is used. Note that on L2, there should be existing smart contract present for this function to run
3. For bridging new ERC20 assets, first it deploys token contract on L2 via createStandardL2Token function of OptimismMintableERC20Factory. Then it calls approve function of ERC-20 contracts
   and then bridge the tokens. Note that there are 3 network changes if goerli network is selected previously and 3 contract calls.
