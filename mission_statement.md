Diverse Memory Kinds in C++
===========================

C++ lives in a world of flat, homogeneous memory. This model has not aged
particular. There are a number of use cases that would benefit from standard
facilities for manipulating **diverse memory kinds**, such as:

* Memory mapped I/O.
* Remote direct memory access.
* Persistent storage of C++ objects.
* Shared memory interprocess synchronization and communication.
* Controlling placement and migration of memory in hierarchical non uniform memory system.

To enable these use cases, we would need to evolve the C++ programming language:

0.) Extend the C++ memory model and abstract machine to support diverse memory kinds.
1.) Placing and using C++ objects (including synchronization objects) in diverse memory.
2.) Controlling and querying properties of diverse memory.
3.) Synchronization of diverse memory to underlying storage.

Here are some concrete features that could be built in this space:

* Interfaces for mapping files and persistent memory into process memory and associated `Allocator`s.
* Mechanisms for querying, setting and requesting attributes of diverse memory regions.
* Support for using `std::atomic`, `std::mutex`, etc in memory shared between multiple C++ processes.
* Fancy pointers and spans which parameterize how diverse memory is accessed.
* Interfaces for flushing/synchronizing writes to diverse memory regions.
* Interfaces for discovering memory hierarchy, and allocating and migrating memory regions within the hierarchy.
* Asynchronous forms of the above, e.g. facilities for asynchronous reads, writes and barriers to remote/persistent memory/memory-mapped files.

Some WG21 papers have been written on topics in this domain:

* [P1026R0](https://wg21.link/P1026R0): A Call for a Data Persistence Study Group
* [P0796R1](https://wg21.link/P0796R1): Supporting Heterogeneous & Distributed Computing Through Affinity  
* [P0567R0](https://wg21.link/P0567R0): Asynchronous Managed Pointer for Heterogeneous Computing
* [P1031R0](https://wg21.link/P1031R0): Low Level File I/O Library

The following WG21 members are interested in this subject area and are willing to spend time on it:

* Bryce Adelstein Lelbach, PL22.16, NVIDIA

