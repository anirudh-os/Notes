# Network Architecture

## OSI Model

- The Open Systems Interconnections (or better known as OSI) model was proposed by ISO (Interenational Systems Organisation)

- It has seven layers

- The communicative functions are partitioned into these `hierarchial` set of layers

- It is created in order to have a design in which changes made in one layer do not affect the other layers

- There are two major divisions in this model:
    1. The host-to-host division: It only exists in the source and destination

    2. The point-to-point division: It exists in the intermediate nodes

### Point to Point Division

#### Physical Layer

- It establishes a connection between two nodes in the physical medium

#### Data Link Layer

- It mainatins the reliable transfer of data over a point-to-point link

- Data unit at this level is a `frame`

- It checks for errors and resolves them

- It also controls the flow of data

#### Network

- Establishing, maintaining and terminating connections

- Routing of packets through various point-to-point links

### Host to Host Division

### Transport Layer

- End-to-End reliable data transfer

- Error recovery and flow control

### Session Layer

- The period of connection between two hosts is called a `session`

- The session layer manages such sessions

### Presentation Layer

- Its an optional layer

- We can handle tasks like adding extra encryption or correct the codes

### Application Layer

- Some application which uses the network for data transmission

## Data Flow

![Data Flow](<assets/Data Flow diagram.png>)

- Since the flow of info is 1-way in one turn, its similar to a stack and therefore it is called a `network stack`

## Internetworking Devices

1. Hub

2. Bridge / Layer 2 Switch

3. Router / Layer 3 Switch