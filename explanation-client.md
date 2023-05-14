# Client Code 

We can devided into 3 parts 

## Header files : 

    conatins all the necessary liberaries for the C program to run , including the port number the maximum size of the message

## Communication function : 

    This is the function that handles the communication between the client and the server.
    sockfd is the file descriptor of the socket that the client uses to communicate with the server.
    The function uses a loop to continuously send and receive messages until the client types "exit".
    bzero() is used to clear the buffer before receiving a message.
    The client is prompted to enter a string to send to the server using printf() and getchar().
    The message is sent to the server using write().
    The buffer is cleared again using bzero().
    The message from the server is received using read().
    The message from the server is displayed using printf().
    If the message received from the server is "exit", the loop is terminated.
    
## The main : 

    sockfd is the file descriptor of the socket that the client uses to communicate with the server.
    servaddr is the struct sockaddr_in structure that holds information about the server's IP address and port number.
    socket() is used to create a socket and returns a file descriptor that is stored in `sockfd.
    If socket() returns -1, it means that the socket creation has failed and the program exits.
    If socket() returns a file descriptor, a success message is printed.
    bzero() is used to clear the servaddr structure.
    The IP address of the server is set to inet_addr(""), which means that the client will connect to the server on the same machine.
    The port number of the server is set to PORT.
    connect() is used to establish a connection between the client and server using the sockfd file descriptor and the servaddr structure.
    If connect() returns a non-zero value, it means that the connection has failed and the program exits.
    If connect() returns zero, a success message is printed.
    The func() function is called to handle the communication between the client and server.
    Finally, close() is used to close the socket.
    
    
    
  ## other details : 
  
  
    socket(): This function creates a new socket and returns a file descriptor that can be used to identify the socket in all later function calls.

    socket(int domain, int type, int protocol)

    Parameters:
        domain: the communication domain, such as AF_INET (IPv4) or AF_INET6 (IPv6).
        type: the communication semantics, such as SOCK_STREAM for reliable, connection-oriented communication, or SOCK_DGRAM for unreliable, message-oriented communication.
        protocol: the protocol to be used with the socket, such as IPPROTO_TCP for TCP or IPPROTO_UDP for UDP.

    bzero(): This function sets the first n bytes of the buffer pointed to by s to zero.

    void bzero(void *s, size_t n)

    Parameters:
        s: a pointer to the buffer to be zeroed.
        n: the number of bytes to be zeroed.

    inet_addr(): This function converts an IPv4 address in dotted decimal notation (such as "127.0.0.1") to a binary representation.

    in_addr_t inet_addr(const char *cp)

    Parameters:
        cp: a pointer to a string containing the IPv4 address in dotted decimal notation.

    htons(): This function converts a 16-bit number from host byte order to network byte order (which is big-endian).

    uint16_t htons(uint16_t hostshort)

    Parameters:
        hostshort: the 16-bit number to be converted.

    connect(): This function establishes a connection to a remote socket.

    int connect(int sockfd, const struct sockaddr *addr, socklen_t addrlen)

    Parameters:
        sockfd: the file descriptor of the socket to connect.
        addr: a pointer to the sockaddr structure containing the address of the remote socket.
        addrlen: the length of the address in bytes.

    read(): This function reads data from a file descriptor.

    ssize_t read(int fd, void *buf, size_t count)

    Parameters:
        fd: the file descriptor to read from.
        buf: a pointer to the buffer where the data will be stored.
        count: the maximum number of bytes to read.

    write(): This function writes data to a file descriptor.

    ssize_t write(int fd, const void *buf, size_t count)

    Parameters:
        fd: the file descriptor to write to.
        buf: a pointer to the buffer containing the data to be written.
        count: the number of bytes to write.

    close(): This function closes a file descriptor.

    int close(int fd)

    Parameters:

    fd: the file descriptor to close.
    
        printf(): This function writes formatted output to the standard output stream (stdout).

    int printf(const char *format, ...)

    Parameters:
        format: a string that specifies the format of the output.
        ...: a variable number of arguments that will be inserted into the format string.

    exit(): This function terminates the calling process immediately.

    void exit(int status)

    Parameters:
        status: the exit status of the process.

    getchar(): This function reads a single character from the standard input stream (stdin).

    int getchar(void)

    Parameters: none.

    strncmp(): This function compares the first n characters of two strings.

    int strncmp(const char *s1, const char *s2, size_t n)

    Parameters:
        s1: a pointer to the first string to be compared.
        s2: a pointer to the second string to be compared.
        n: the maximum number of characters to compare.

    func(): This function handles the chat between the client and the server.

    void func(int sockfd)

    Parameters:
        sockfd: the file descriptor of the socket used for communication.

    main(): This is the main function of the program.

    int main(void)

    Parameters: none.
