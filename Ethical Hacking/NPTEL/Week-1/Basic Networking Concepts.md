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

* 