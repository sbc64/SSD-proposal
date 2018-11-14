## Simple SubnetDAO proposal

### What a subnetdao does

A subnetdao has three functionalities:

 1. Administrate, via a multisig, a hash map of ipv6 with their corresponding ethereum address.
 2. Collect fees from members of this hash map.
 3. Capability to admistrate collected fees for the subnetDAO owners.

### Current subnetDAO implementation

Althea has been using Aragon as their subnetDAO framework. Aragon provides an easy (compared with other DAO frameworks availabel) framework for creating complex DAOs. Functionality such as upgradeability of Aragon apps, permissions, and multiple apps that could cooperate ina single DAO.

This has been too much functionality for a simple implementation of a subnetdao.

### Possible implementations of subnetdaos

1. Gnosis safe team edition.

    * Use built in multisig
    * Txn relayer, using erc20 to pay for gas, but this only usable for the gnosis safe personal edition

2. DIY implementation

    * Multisig contract (probably use an existing multisig contract)
    * Frontend web3 libraries (dapapratus or truffle react)


### SubnetDAO stack when using gnosis safe team edition (GSTE)

The current [UI of gnosis safe](https://github.com/gnosis/safe-react) is using the GSTE. Essentially it is a multisig interface that handles cryto assets. The contracts for gnosis safe are in a single repo so an implementation of a subnetdao could be the following:

1. The same [smart contract](https://github.com/althea-mesh/aragon-node-list/blob/master/contracts/Althea.sol) used in the current aragon dao implementation.

2. Build own althea frontend using dapparatus or truffle drizzle.
    * Porting the current althea aragon app frontend.
    * Upon initialization, this front end calls the same steps that the GSTE calls to deploy a multisig wallet of the [safe contracts](https://github.com/gnosis/safe-contracts) plus it also deploys the existing subnetdao contract. This subnetdao contract will be owned by the multisig.
3.  When a subnet users wants to check their status on the subnet. They could either access the domain of the subnetdao. which directly points to the its own contracts. Each subnetdao will need their own domain and hosting capabilities. A single website for all of the Althea subnetdaos is possible but out of scope for now.


### TCR considerations

When the TCR for Althea gets released this TCR will curate the multisig contracts that want to be part of the TCR.


### Warnings

It seems that the gnosis safe is still under development and that they might also suffer from, perfect developement cycle (they never have to maintain a LTS) where they just push new code out, because of their succesful million dollar ICO.