---
description: >-
  Simple answer, docker is the preferred and supported containerization platform
  for running Presearch nodes.
---

# Is Docker required to run a Presarch node?

> **Warning:** It is against the Presearch Terms of Service to modify the Presearch software on any node that is added to the network. Doing so may lead to forfeiture of tokens staked within your account.

Docker is a critical part of the node delivery process and not an arbitrary layer we've added on top.&#x20;

Main advantages for choosing Docker:

* **consistency** - works the same across all node operators for x64 and arm64 architectures&#x20;
* **simplicity** - allows us to execute one command or line of instructions to start a node
* **security -** we can validate the environment and ensure there are no malicious actors
* **supportability** - we have a small team and support for several dozen other platforms or complicated configuration across multiple operating systems is not the way we can accomplished
* **future-proofing** - the node will need to run several software systems internally for indexing, searching, routing, etc., well beyond a single "node" app, but an entire ecosystem of services

Docker simplifies our ability to deliver and support a consistent and reliable node platform and evolve it to keep the node operator process simple and consistent as we evolve.

Using Docker is free to use, the main engine part is released under Apache 2.0 licences. For instructions on how to set up a search node, check out our [instructions](https://nodes.presearch.org/instructions).
