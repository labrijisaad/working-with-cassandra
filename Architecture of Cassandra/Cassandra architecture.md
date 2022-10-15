# `Architecture of Cassandra` ✏️

The **Apache Cassandra architecture** is designed to provide **scalability**, **availability**, and **reliability** to **store massive amounts of data**.

## `Apache Cassandra Topology`
- **Cassandra** is based on a **distributed system architecture**. In its simplest form, *Cassandra can be installed on a single machine or container*. A single Cassandra instance is called a *node*. Cassandra supports **horizontal scalability** achieved by adding more than one node as a part of a Cassandra cluster.  
- 
<p align="center">
    <img src="https://user-images.githubusercontent.com/74627083/195995622-faed8b33-a1ac-4f9b-82e0-9478d2acfafb.png"/>
</p>

- As well as being a **distributed system**, Cassandra is designed to be a **peer-to-peer architecture**, with each node connected to all other nodes. Each Cassandra node can perform all database operations and can serve client requests without the need for a primary node.  
- **peer-to-peer architecture**: nodes are both clients and servers.

<p align="center">
    <img src="https://user-images.githubusercontent.com/74627083/195995825-aa5c4e06-5bcd-4846-b786-7942a1b15c3a.png"/>
</p>

- **How do the nodes in this peer-to-peer architecture (no primary node) know to which node to route a request and if a certain node is down or up?** Through `Gossip`. 
- `Gossip` is the protocol used by **Cassandra nodes** for **peer-to-peer communication**. 
- The **gossip protocol** informs a *node* about the state of all *other nodes*. 
- A *node* performs **gossip communications** with up to three *other nodes* every second. 
- The **gossip** messages follow a specific format and use version numbers to make efficient communication, thus shortly *each node can build the entire metadata of the cluster* (which nodes are up/down, what are the tokens allocated to each node, etc..). 

## `Multi Data Centers Deployment`
- A **Cassandra cluster** can be a **single data center deployment** (like in the above pics), but most of the time Cassandra clusters are deployed in **multiple data centers**. 
- A `multi data-center deployment looks` like below – where you can see depicted a 12 nodes Cassandra cluster, topology wise installed in 2 datacenters. Since replication is being set at keyspace level, demo keyspace specifies a replication factor 5: 2 in data center 1 and 3 in data center 2.   

<p align="center">
    <img src="https://user-images.githubusercontent.com/74627083/195996488-d9d80204-e720-4787-8418-96bb6f5c3283.png"/>
</p>

- **Note**: since a Cassandra node can be as well a **coordinator** of operations, in our example since the operation came in data center 2 the node receiving the operation becomes the coordinator of the operation, while a node in data center 1 will become the **remote coordinator** taking care of the operation in only data center 1.  

## `Components of a Cassandra Node` 
There are several components in Cassandra nodes that are involved in the write and read operations. Some of them are listed below: 


https://www.coursera.org/learn/introduction-to-nosql-databases/supplement/aIdzT/architecture-of-cassandra











## `Author`
<a href="https://www.linkedin.com/in/labrijisaad/" target="_blank">Saad LABRIJI</a>


## `Change Log`
| Date (YYYY-MM-DD) | Version | Changed By    | Change Description                                 |
| ----------------- | ------- | ------------- | -------------------------------------------------- |
| 2022-10-15        | 1.0     | Labriji saad  | Added the Architecture                             |




