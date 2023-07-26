# linux-net-lib

A high-performance, multi-threaded, non-blocking, C++ networking library for Linux servers. Encapsulate the networking layer (epoll, event loop, and thread pool design) to allow user applications to implement server and client classes for processing connecting/disconnecting, and read/write events. Call client callbacks upon changes in the networking system.

## Features
* I/O multiplexing to handle multiple I/O streams simultaneously
* Non-blocking event loop to reduce CPU idle time 
* Thread pool to take advantage of modern multi-core architecture
* Synchronization and mutual exclusion between threads
* Reactor design pattern to handle high-concurrency service requests
* Enhanced performance with modern C++ features
* Example library for a test server


## Usage
Source and header files are compiled to a .so library in /lib/liblinuxnet.so
To import the headers and add the shared library to the include path:
```console
user@linux-machine:~$ ./autobuild.sh
```
To run the test server the links with liblinuxnet.so
```console
user@linux-machine:~$ cd example
user@linux-machine:~$ make testserver
```
![Client-Server TCP Connection Established](https://github.com/chuhan-ouyang/linux-net-lib/assets/112202738/ecb8635f-a5d9-4f7e-957c-4d3f206ef52b)
Client-Server TCP Connection Established
![Echo Server: Server Side](https://github.com/chuhan-ouyang/linux-net-lib/assets/112202738/5d750685-344c-49ad-8a74-e960d764ba22)
Echo Server: Server Side 
![Echo Server: Client Side](https://github.com/chuhan-ouyang/linux-net-lib/assets/112202738/84131f51-8ff8-4bbc-af64-1103086e75f2)
Echo Server: Client Side

