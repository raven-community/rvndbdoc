---
id: decentralized
title: RvnDB vs. Other Decentralized Projects
sidebar_label: RvnDB vs. Other Decentralized Projects
---

---

## "Decentralized Database"

Most attempts at building a "global decentralized database" have looked like this:

1. take an existing data storage solution that supports replication
2. implement the replication feature
3. sprinkle some magical distributed consensus and governance rules to tackle the decentralized replication problem.

![concurrent write](assets/concurrentwrite.png)

The big challenge with this approach is that the network needs to not only get the tech but also the incentive structure right in order to achieve decentralization. If nobody is incentivized enough to run the network, the whole thing collapses overnight. This is not a trivial problem. There's a reason why we don't have a mainstream decentralized database with such architecture.

Bitdb does not invent a new experimental consensus algorithm, nor does it try to bootstrap a new network from scratch starting from 0 liquidity, all of which are huge risk factors for these initiatives.

Because Ravencoin has already solved the decentralized consensus problem through Proof of Work, Bitdb works right out of the box, because RvnDB is Ravencoin.

---

## RvnDB

One of the main reasons why these decentralized database or blockchains don't use proof of work is because they think that proof of work doesn't scale.

RvnDB is a project to show that:

- It is not only possible to build a scalable decentralized app on top of proof of work
- But actually, proof of work is THE ONLY IDEAL way to build **truly decentralized** apps.

RvnDB builds on top of Ravencoin.

![one way sync](assets/onewaysync.png)

### 1. RvnDB is Proof of Work

Bitdb utilizes Ravencoin as the single source of truth, and the "database" is just a derived layer on top of the Ravencoin's blockchain, providing a high level, high throughput readonly API into Ravencoin.

RvnDB can only be derived from Ravencoin (Only RvnDB can write to itself by reading from Ravencoin, and humans can't write to RvnDB directly) therefore the contents inside RvnDB are transactions confirmed by Ravencoin's proof of work.

Application developers can also potentially apply additional measures to improve security, such as:

1. **Trust but verify:** Each RvnDB document contains a transaction hash, so applications can cross-validate RvnDB content directly with any available Ravencoin node.
2. **Multi-node cross-validation:** Cross-validate a RvnDB document against multiple other RvnDB nodes to check for discrepancies

### 2. RvnDB is Readonly

One of the key distinctions with RvnDB compared to all other "decentralized" projects is that RvnDB does not try to reinvent what's already solved. It doesn't come up with a scheme to solve the problem of concurrent writes to the single source of truth, it only reads from it.

You can't directly write to RvnDB. Only entity that can write to RvnDB is itself, by auto-synchronizing with Ravencoin. So if you want to write to RvnDB, you just need to make a Ravencoin transaction, and it will immediately synchronize.

This "readonly" and "one way synchronization" aspect is important because the act of writing is where all the convolution and complexity arises in other systems, and is exactly the problem Ravencoin has solved gracefully.

### 3. Conclusion

RvnDB's read action is powered by flexible NoSQL database.

RvnDB's write action is powered by Ravencoin's Proof of Work.

RvnDB brings the efficiency of centralized databases while providing the security of Ravencoin's Proof of Work, by being one-way pegged to Ravencoin.
