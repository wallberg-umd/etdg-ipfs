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
## Emerging Technology Discussion Group
## December 5, 2017

-- 

### IPFS - Content Addressed, Versioned, P2P File System

The InterPlanetary File System (IPFS) is a peer-to-peer distributed file system that seeks to connect all computing devices with the same system of files. In some ways, IPFS is similar to the Web, but IPFS could be seen as a single BitTorrent swarm, exchanging objects within one Git repository.

[IPFS White Paper](https://github.com/ipfs/papers/raw/master/ipfs-cap2pfs/ipfs-p2p-file-system.pdf)

--

### Introduction: InterPlanetary File System

Initially designed by Juan Benet, developed since 2014 by [Protocol Labs](https://protocol.ai/) with help from the open-source community.

Alpha Release

Synthesis of existing concepts and technologies

Aims to become the next generation distributed web, replacing HTTP

--

### Introduction: InterPlanetary?

* no other planets participating, yet
* designed for scale, globally and beyond

--

### Introduction: Resources

* [ipfs.io](https://ipfs.io)
* [Decentralized Web Primer](https://flyingzumwalt.gitbooks.io/decentralized-web-primer/content/)
* [IPFS GLAM Community](https://github.com/ipfs-shipyard/ipfs-glam-community)

--

### Introduction: Code4Lib Conference

* I learned about IPFS at the 2017 conference
* Washington, D.C, February 13-16, 2018
* http://2018.code4lib.org/
* multi-day ETDG!

--

### Concept: Content Addressed

* Not device addressed, as in the hostname of the URL (eg, www.lib.umd.edu)
* Addressed by the cryptographic hash of the content

--

### Concept: Content Addressed

Hash Function

Maps data of arbitrary size (message) to data of fixed size (hash)

https://en.wikipedia.org/wiki/Hash_function

--

### Concept: Content Addressed

Cryptographic Hash Function

* same input message always produces the same hash
* quick to compute
* infeasible to reverse
* a small change to the message results in large change to the hash
* infeasible to find two messages with the same hash

https://en.wikipedia.org/wiki/Cryptographic_hash_function

-- 

### Demo: Getting Started

Install using Homebrew for Mac OS X
```
brew install ipfs
```

Initialize the local repository
```
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

(message = IPFS header + the image file)

--

### Demo: Getting files out

Get the file back out (addressed by hash)

```
ipfs cat <hash> | open -f -a /Applications/Preview.app
```

Get it from the global gateway?

```
curl https://ipfs.io/ipfs/<hash>
```

Hash of the picture taken in the ETDG meeting:
```
QmSMjLHHGL24mHwjDY9Z4bpn6xfwaniFQqUbSeQaiogzhf
```

[https://ipfs.io/ipfs/QmSMjLHHGL24mHwjDY9Z4bpn6xfwaniFQqUbSeQaiogzhf](https://ipfs.io/ipfs/QmSMjLHHGL24mHwjDY9Z4bpn6xfwaniFQqUbSeQaiogzhf)
--

### Concept: Peer-to-Peer (P2P)

* Like BitTorrent: swarm of peers
* Like BitTorrent: files distributed as chunks
* But, no central torrent file

![Unstructured, peer-to-peer network diagram](295px-Unstructured_peer-to-peer_network_diagram.png)

[CC0 1.0](https://en.wikipedia.org/wiki/File:Unstructured_peer-to-peer_network_diagram.png)

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

Or grab a local copy
```
ipfs get <hash>
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

--

### Concept: Merkle Directed Acyclic Graph (DAG) 

* Graph: network of nodes (vertices) connected to each other (edges)
* Directed: Links go from one node to another (and not the reverse)
* Acyclic: No cycle back to a previous node
* Merkle: includes hashes

--

### Concept: Merkle Directed Acyclic Graph (DAG) 

Like Git - [Git Book](https://git-scm.com/book/en/v2/Git-Internals-Git-Objects)

![Git Data Model](git-data-model-3.png)

--

### Concept: Files

1. block:  a variable-size block of data.
2. list: a collection of blocks or other lists.
3. tree: a collection of blocks, lists, or other trees.
4. commit: a snapshot in the version history of a tree.

-- 

### Demo: Merkle DAG / Files

Traverse the graph for the quick start video folder
```
ipfs ls -v QmTKZgRNwDNZwHtJSjCp6r5FYefzpULfy37JvMt9DwvXse
ipfs ls -v QmRS3Ts9HGTPrNyvHc8GujKJRa3znuEANvE8eK8bdUDAGo
ipfs ls -v QmQkHpST7LL6zeLkVTFgTmSdbmnQaD8iWkutLhe9UHUvwq
ipfs ls -v Qma4yxBN8gMB3GotHuM2hhRJ3nZRXr1Pdrj9Fsh1hyKQQT
```

Or visit the [web interface to your local daemon](http://localhost:5001/ipfs/QmPhnvn747LqwPYMJmQVorMaGbMSgA7mRRoyyZYz3DoZRQ/#/objects/\ipfs\QmTKZgRNwDNZwHtJSjCp6r5FYefzpULfy37JvMt9DwvXse)

--

### Concept: Immutability & Versioning

Different versions hash differently

--

### Concept: IPNS

InterPlanetary Naming System

Add a small amount of mutability to the permanent immutability that is IPFS

--

### Concept: IPNS

IPNS is a [PKI](https://en.wikipedia.org/wiki/Public_key_infrastructure) namespace, where names are the hashes of public keys, and the private key enables publishing new (signed) values. 

Te default name used is the node's own PeerID, which is the hash of its public key. 

--

### Demo: IPNS

```
ipfs id
```

[See IPNS example](https://ipfs.io/docs/examples/example-viewer/example#../ipns/readme.md)

--

### Demo: IPNS

Also, utilize the DNS system with TXT records

```
dig TXT ipfs.io
ipfs dns ipfs.io
```

--

### Use Cases

* [Datasets](https://awesome.ipfs.io/datasets/)

* [Catalonian Referendum](https://gateway.ipfs.io/ipfs/QmQZzfs7LjkEnmG3zU92YF7ViCcuCXkNokuYoiNe6pKvDZ/en/index.html)

* [InterPlanetary Wayback (ipwb)](https://github.com/oduwsdl/ipwb) - facilitates permanence and collaboration in web archives by disseminating the contents of WARC files into the IPFS network.

* [ipscend](https://ipfs.io/blog/3-ipscend/) - Publish static web content

* [ipfs-cluster](https://github.com/ipfs/ipfs-cluster) - Collective pinning and composition (Preservation requires copies)
