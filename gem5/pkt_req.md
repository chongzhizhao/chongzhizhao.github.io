# Understanding `Packet` class and `Request` class in gem5

## `Packet` class

A packet is used to encapsulate a transaction between 2 objects in the memory system.

`headerDelay` is the extra delay from seeing the packet until the header is transmitted. 

`payloadDelay` is the extra pipelining delay from seeing the packet until the end of
payload is transmitted by the component that provided it (if any). This includes the
header delay. Similar to the header delay, this is used to make up for the fact that the
crossbar does not make the packet wait. As the delay is relative, a 32-bit unsigned
should be sufficient. 

## `Request` class

A request travels all the way from the requestor to the ultimate destination and back,
possibly conveyed by several different packets along the way.
