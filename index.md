title: InterPlanetary File System | ETDG
date: 2017-12-05
author:
  name: Ben Wallberg
  email: wallberg@umd.edu
  url: https://wallberg-umd.github.io/etdg-ipfs/
theme: theme
output: index.html

--

# InterPlanetary File System
##Emerging Technology Discussion Group
##December 5, 2017

-- 

### InterPlanetary File System

Initially designed by Juan Benet, developed since 2014 by [Protocol Labs](https://protocol.ai/) with help from the open-source community.

Alpha Release

Synthesis of existing concepts and technologies

--

### IPFS - Content Addressed, Versioned, P2P File System

The InterPlanetary File System (IPFS) is a peer-to-peer distributed file system that seeks to connect all computing devices with the same system of files. In some ways, IPFS is similar to the Web, but IPFS could be seen as a single BitTorrent swarm, exchanging objects within one Git repository.

[IPFS White Paper](https://github.com/ipfs/papers/raw/master/ipfs-cap2pfs/ipfs-p2p-file-system.pdf)

--

### InterPlanetary?

* no other planets participating, yet
* designed for scale, globally and beyond

--

### Resources

* [ipfs.io](https://ipfs.io)
  * [Homepage copy via IPFS public gateway](https://ipfs.io/ipfs/QmVb7nota99V3ypeX63eS6bAZLUQ42Gg5W6jXdRvhJh2u3/index.html)
  * [Homepage copy via IPFS local daemon](http://localhost:8080/ipfs/QmVb7nota99V3ypeX63eS6bAZLUQ42Gg5W6jXdRvhJh2u3/index.html)
* [Decentralized Web Primer](https://www.gitbook.com/book/flyingzumwalt/decentralized-web-primer/details)
--

### Code4Lib Conference

And now for some shameless advertising

* I learned about IPFS at the 2017 conference
* Washington, D.C, February 13-16, 2018
* http://2018.code4lib.org/
* multi-day ETDG!

--

### Concept: Content Addressed

* Not device addressed
* Hashing (Qm?)

--

### Concept: Peer-to-Peer (P2P)

* BitTorrent
* Swarm of peers
* Chunked

--

### Concept: Git / Merkle DAG 

--

### Concept: Immutability

--

### Demo: Getting Started

```
brew install ipfs
ipfs init
ipfs id
ipfs swarm peers
```

--



