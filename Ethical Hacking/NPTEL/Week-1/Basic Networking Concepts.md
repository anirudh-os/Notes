# Computer Networks

## Types of Networks

1. LAN
2. MAN
3. WAN

## Working

### 1. Circuit Switching

* Old method
* A dedicated path between the source and destination is established
* The sequence of nodes is fixed
* A logical channel is created on each physical link (dedicated to that particular connection)
* Steps needed for communication:
    1. Connection Establishment
    2. Data Transfer
        * Since there is a dedicated amount of banvdwidth set for each link, the data transfer happens at the maximum possible speed (of the bandwidth) without any disruption
    3. Connection Termination
        * The resources allotted to the connection are deallocated and can be used for another connection
* Drawbacks:
    * Entire channel is dedicated for a single connection which is very ineffiient in case of data transfer which happens in bursts
    * There is an initial delay as the communication establishment needs to take place

### 2. Packet Switching

* It is a modern form of Network Communication
* There is no use of dedicated network resources
* Links can be shared
* Data is transmitted in short packets
    * The long message is divided into chunks called packets
    * Each packet has 2 parts:
        1. Header: Which contains the information about the packet
        2. Content: It has a part of the longer message which has been divided
* These packets are transmitted one by one, rather than the whole message at once
* This method is based on store-and-forward concept:
    * Each node stores the data it recieves temporarily in buffer
    * It decides the route in which the packet will be sent to another link (There can be multiple links)
    * If the route is not busy, it will then forward it in that route
    * The decision of routes is done using the `routing table` which each node maintains
* Advantages:
    * Link utilization is better as no links are reserved
    * Suitable for computer generated traffic which is bursty in nature
    * Buffering and data rate can be performed easily

### Ways of implementing Packet switching:

#### 1. Virtual Circuit

* Analogical to a telephone system
* A route is established priorly
* Packets are forwarded using the store-and-forward concept
* A virtual circuit number is carried by each packet which is generated during the route establishment.
    * It denotes the route in which the packet is to be transmitted
* No dynamic route decision is taken

#### 2. Datagrams

* No route is established beforehand 
* Each packet is transmitted as an independant entity
* no history is maintained
* Analogical to a postal system
* Every intermediate node takes the routing decision dynamically
    * Each node maintains a `routing table`
    * Each packet must have a source and destination address
* Problems:
    * Packets might get delivered out of order
    * If an intermediate node goes down, the queued packets are lost
    * Duplicate packets might get generated
* Advantages:
    * Faster than virtual circuits for smaller number of packets
    * More flexible and hence, can handle congestion/failed link
    * Packets can follow different paths

### Comparitive Study

#### Delays

1. Propagation Delay:
    * The time taken for the signal to reach from one node to another
2. Transmission Delay
    * Time taken for the node to transmit the signal
    * Measured in bits/sec
3. Processing Delay
    * The time needed for the packet to recieve, store and decide the route for the packet

#### Circuit Switching

* Initial delay due to connection establishment
* After that the connection proceeds at the maximum speed

#### Virtual Circuit

* A `call request` packet is sent from source to destination
    * This will help in setting up the routing tables for all the intermediate nodes for that particular virtual circuit number
* A `call accept` packet is returned from the destination once the connection is established
* These lead to an initial delay in the connection

#### Datagram Packet Switching

* No intial delay as there is no process of connection establishment
* The packets are transmitted independently and may follow different paths 