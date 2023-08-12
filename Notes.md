Asyncrhonous I/O

Non-Blocking I/O

Epoll
* epoll is a system call and I/O event notification facility in Linux-based operating systems that is used for efficiently managing large numbers of file descriptors or sockets. It is particularly designed for scalable and high-performance I/O operations, commonly used in server applications that need to handle a large number of concurrent connections.
* The epoll mechanism allows a program to monitor multiple file descriptors (sockets or other types of I/O handles) for various types of events, such as data availability for reading or writing, error conditions, and the ability to initiate a new connection. It's an improvement over older event notification mechanisms like select and poll which have limitations in terms of scalability and performance.
* Here are some key concepts related to epoll:
  * Event-driven Architecture: epoll follows an event-driven architecture, where your program registers interest in specific events on multiple file descriptors. When these events occur, your program is notified, allowing it to take appropriate actions.
  * File Descriptors: In Unix-like systems, file descriptors are used to represent I/O resources such as sockets, files, pipes, etc. epoll works with these file descriptors to monitor I/O events.
  * Edge-Triggered and Level-Triggered Modes: epoll can work in either edge-triggered mode or level-triggered mode. In edge-triggered mode, an event is reported only when there's a change in the state of the file descriptor (e.g., new data arrives). In level-triggered mode, the event is reported as long as the condition is true (e.g., data is available).
  * Efficiency: One of the main advantages of epoll is its efficiency when dealing with a large number of file descriptors. It uses a scalable data structure to manage events, reducing the overhead of iterating through file descriptors like in select or poll.
  * Asynchronous I/O: By using epoll, you can build non-blocking, asynchronous I/O systems efficiently. This is crucial for applications that need to handle many concurrent connections without resorting to creating a separate thread or process for each connection.
  * Usage in Network Servers: epoll is often used in network servers, where the server needs to listen for incoming connections, read and write data to and from multiple clients, and manage a significant number of simultaneous connections.


Networking Basics
* InetAddress is a concept and often a class provided by programming libraries and frameworks, commonly used in network programming to represent an IP address. 
  * It's a fundamental element when dealing with networking in computer programming.
* Socket (IP + PORT) is a communication endpoint that allows processes to communicate with each other,
either on the same machine or across a network. Sockets are a fundamental concept in network programming and are used for inter-process communication (IPC) as well as network communication.
  * Stream Sockets (TCP/IP): Stream sockets provide reliable, connection-oriented communication using the TCP (Transmission Control Protocol) protocol. They ensure that data is delivered in the same order it was sent and that no data is lost. TCP sockets are commonly used for applications that require reliable and ordered data transmission, such as web browsing, file transfer, and email.
  * Datagram Sockets (UDP/IP): Datagram sockets provide connectionless communication using the UDP (User Datagram Protocol) protocol. They are useful when you need fast communication with lower overhead, but without the guarantees of reliability and ordering that TCP provides. UDP sockets are used in scenarios like streaming media, online gaming, and situations where speed is prioritized over reliability.
```cpp
struct sockaddr_in {
    short int sin_family;         // Address family (AF_INET)
    unsigned short int sin_port; // Port number (network byte order)
    struct in_addr sin_addr;     // IP address (32-bit)
    unsigned char sin_zero[8];   // Padding to make the struct size equal to sockaddr
};
```
* IP Address vs. Sockets
  * IP Address: An IP address (Internet Protocol address) is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication.
It uniquely identifies a device on a network, allowing data to be routed between different devices.
IP addresses come in two main versions: IPv4 (32-bit addresses) and IPv6 (128-bit addresses). IPv4 addresses are more common and are typically represented in dotted-decimal notation (e.g., 192.168.1.1), while IPv6 addresses are represented in hexadecimal (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).
IP addresses are fundamental for network communication, but they don't include information about specific ports or processes on a device.
  * Socket Address: A combination of an IP address and a port number.
It uniquely identifies a specific endpoint for communication in a network.
In the context of the Berkeley Sockets API, a socket address is typically represented using structures like sockaddr and sockaddr_in (for IPv4) or sockaddr_in6 (for IPv6).
The socket address specifies the destination or source of data when communicating over a network. It includes both the IP address and the port number, which indicates the specific application or service on a device.
Socket addresses are essential for establishing connections between processes over a network. They allow data to be sent to the correct destination within a device.
In summary, an IP address identifies a device on a network, while a socket address identifies a specific communication endpoint on that device. Socket addresses include both the IP address and the port number to facilitate communication between applications or services running on the device.\
* File Descriptors: A file descriptor (often abbreviated as "fd") is a unique identifier used by the operating system to access files, devices, and other I/O resources. It serves as a handle that programs use to interact with these resources. File descriptors are used not only for files but also for other I/O operations, including sockets, pipes, and more.
  * In Unix-like systems, file descriptors are represented as non-negative integers. They are managed by the operating system and stored in a per-process table. Standard input, standard output, and standard error (stdin, stdout, and stderr) are also represented as file descriptors (0, 1, and 2 respectively) by default.
* FD vs. Sockets
  * When it comes to networking, sockets are used for sending and receiving data over the network. They are a higher-level abstraction built on top of file descriptors. In fact, sockets are often managed using file descriptors, which is why you'll often see references to file descriptors when dealing with socket operations.
  * A file descriptor is a general concept used to represent various I/O resources, including files and sockets, in Unix-like operating systems. Sockets, on the other hand, are specifically used for networking communication, enabling data exchange between devices over a network. File descriptors are used to manage sockets, making them a core part of socket-based networking programming.

TCP Basics
