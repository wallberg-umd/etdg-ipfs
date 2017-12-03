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

### IPFS - Content Addressed, Versioned, P2P File System

The InterPlanetary File System (IPFS) is a peer-to-peer distributed file system that seeks to connect all computing devices with the same system of files. In some ways, IPFS is similar to the Web, but IPFS could be seen as a single BitTorrent swarm, exchanging objects within one Git repository.

[IPFS White Paper](https://github.com/ipfs/papers/raw/master/ipfs-cap2pfs/ipfs-p2p-file-system.pdf)

--

### Introduction: InterPlanetary File System

Initially designed by Juan Benet, developed since 2014 by [Protocol Labs](https://protocol.ai/) with help from the open-source community.

Alpha Release

Synthesis of existing concepts and technologies

--

### Introduction: InterPlanetary?

* no other planets participating, yet
* designed for scale, globally and beyond

--

### Introduction: Resources

* [ipfs.io](https://ipfs.io)
  * [Homepage copy via IPFS public gateway](https://ipfs.io/ipfs/QmVb7nota99V3ypeX63eS6bAZLUQ42Gg5W6jXdRvhJh2u3/index.html)
  * [Homepage copy via IPFS local daemon](http://localhost:8080/ipfs/QmVb7nota99V3ypeX63eS6bAZLUQ42Gg5W6jXdRvhJh2u3/index.html)
* [Decentralized Web Primer](https://www.gitbook.com/book/flyingzumwalt/decentralized-web-primer/details)
--

### Introduction: Code4Lib Conference

And now for some shameless advertising

* I learned about IPFS at the 2017 conference
* Washington, D.C, February 13-16, 2018
* http://2018.code4lib.org/
* multi-day ETDG!

--

### Concept: Content Addressed

* Not device addressed, as in the hostname of the URL (eg, www.lib.umd.edu)
* Cryptographic Hash of the contents of a file (actually a block)


-- 

### Concept: Content Addressed

IPFS represents the hash of files and objects using Multihash format and Base58 encoding. The letters "Qm" happen to correspond with the algorithm (SHA-256) and length (32 bytes) used by IPFS.

Other algorithms and lengths could be used.

https://github.com/ipfs/faq/issues/22

--

### Concept: Git / Merkle Directed Acyclic Graph (DAG) 

--

### Concept: Immutability & Versioning

Different versions hash differently

--

### Demo: Getting Started

```
brew install ipfs
ipfs init
ipfs cat /ipfs/QmS4ustL54uo8FzR9455qaxZwuMiUhyvMcX9Ba8nUH4uVv/readme
```

--

### Demo: Adding files

Take a picture and it to the local repository

```
ipfs add ~/Pictures/Photo\ Booth\ Library/Pictures/XXX.jpg
```

Copy the resulting hash

--

### Demo: Getting files out

Get the file back out (addressed by hash)

```
ipfs cat <hash> | open -f -a /Applications/Preview.app
```

Get it from the global gateway?

```
curl https://ipfs.io/ipfs/<HASH>
```

--

### Concept: Peer-to-Peer (P2P)

* BitTorrent
* Swarm of peers
* Chunked

--

### Demo: Running the daemon

Connect to the swarm and become a peer in the global network

```
ipfs id
ipfs swarm peers
ipfs daemon
ipfs swam peers
```

Try again to retrieve via the global gateway

```
curl https://ipfs.io/ipfs/<hash> | open -f -a /Applications/Preview.app
```

--

### Demo: Stream a video

```
ipfs cat /ipfs/QmS4ustL54uo8FzR9455qaxZwuMiUhyvMcX9Ba8nUH4uVv/quick-start
ipfs cat QmTKZgRNwDNZwHtJSjCp6r5FYefzpULfy37JvMt9DwvXse/video.mp4 | mplayer -

# Kill the daemon and play again, because cached in the local repo
ipfs cat QmTKZgRNwDNZwHtJSjCp6r5FYefzpULfy37JvMt9DwvXse/video.mp4 | mplayer -

# Remove from the local repo and try again
ipfs repo gc
ipfs cat QmTKZgRNwDNZwHtJSjCp6r5FYefzpULfy37JvMt9DwvXse/video.mp4 | mplayer -

# Restart the daemon to get the video again
```

--

### Demo: mount in the filesystem via FUSE

```
ipfs mount
ls /ipfs/QmS4ustL54uo8FzR9455qaxZwuMiUhyvMcX9Ba8nUH4uVv
more /ipfs/QmS4ustL54uo8FzR9455qaxZwuMiUhyvMcX9Ba8nUH4uVv/about
```








