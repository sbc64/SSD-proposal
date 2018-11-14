## Simple SubnetDAO proposal

### What a subnetdao does

A subnetdao contract has three functionalities:

 1. Administrate, via a multisig, a hash map of ipv6 with their corresponding ethereum address.
 2. Collect fees from members of this hash map.
 3. Capability of admistrating collected fees on behalf the subnetDAO owners.

### Current subnetDAO implementation

Althea has been using Aragon as their subnetDAO framework. Aragon provides an easy (compared with other DAO frameworks availabel) framework for creating complex DAOs. Functionality such as upgradeability of Aragon apps, permissions, and multiple apps that could cooperate ina single DAO.

### Possible implementations of subnetdaos

1. Gnosis safe team edition.
    * The gnosis safe personal edition has meta transaction capabilities which **might** be useful when althea migrates to a stable coin. This allows end users (not subnedao owners) to use only dai.

2. (pending)

#### SubnetDAO stack when using gnosis safe team edition (GSTE)

The current [UI of gnosis safe](https://github.com/gnosis/safe-react) is using the GSTE. Essentially it is a multisig interface that handles cryto assets. The contracts for gnosis safe are in a single repo so an implementation of a subnetdao could be the following:

1. The same [smart contract](https://github.com/althea-mesh/aragon-node-list/blob/master/contracts/Althea.sol) used in the current aragon dao implementation.

2. Build our own Althea frontend using [pdapparatus](https://github.com/austintgriffith/dapparatus) or [truffle drizzle](https://truffleframework.com/drizzle).
    * Port the current Althea aragon app frontend to not use Aragon UI components.
    * Upon initialization, this front end calls the same steps that the GSTE calls to deploy a multisig wallet of the [safe contracts](https://github.com/gnosis/safe-contracts) plus it also deploys the existing subnetdao contract. This subnetdao contract will be owned by the multisig.
    * The ui will also need a way of executing external contract calls from the GSTE multsig. This capability already exists within the contacts, it just needs the frontend for it.
3.  When a subnet users wants to check their status on the subnet, they can access the domain of the subnetdao.This domain points to the its own subnetdao contracts. Each subnetdao will need their own domain and hosting capabilities. A single website for all of the Althea subnetdaos is possible but out of scope for now.


### TCR considerations

When the TCR for Althea gets released this TCR will curate the multisig contracts that want to be part of the TCR.


### Warnings

It seems that the gnosis safe is still under development and that they might also suffer from, perfect developement cycle (they never have to maintain a LTS) where they just push new code out, because of their succesful million dollar ICO.