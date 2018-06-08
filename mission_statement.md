Diverse Memory Kinds in C++
===========================

Modern computing systems are increasingly heterogeneous. The memory seen by a
C++ process consists of multiple types and kinds. Some layer on top of others
e.g. CPU cache memory on top of main memory. Some have very different access
times e.g. NUMA and fabric and storage connected memory. Some are shared
resources, and thus must be managed for concurrency. Some must be interruption
safe, as they contain contents whose intact survival is particularly valuable
to the user of the C++ process.

However, the C++ standard does not have formal support for any of these
**diverse memory kinds**. Today, C++ lives in a world of flat, homogeneous
memory - a model has not aged particularly well and is woefully inadequate for
platforms with hierarchal memory, interprocess communication or memory-mapped
I/O.

There are a number of use cases that would be enabled from standard facilities
for manipulating diverse memory kinds, such as:

* Memory mapped I/O.
* Remote direct memory access.
* Persistent storage of C++ objects.
* Shared memory interprocess synchronization and communication.
* Controlling placement and migration of memory in hierarchical non uniform memory system.

To enable these use cases, we would need to evolve the C++ programming language:

* Extend the C++ memory model and abstract machine to support diverse memory kinds.
* Enable placing and using C++ objects (including synchronization objects) in diverse memory.
* Enable controlling and querying properties of diverse memory.
* Provide facilities for synchronization in diverse memory.

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

* Bryce Adelstein Lelbach
* Niall Douglas

