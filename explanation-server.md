# Server Code 

We can devided into 3 parts 

## Header files : 

    conatins all the necessary liberaries for the C program to run , including the port number the maximum size of the message

## Communication function : 

    responsible for handling the communication between the client and the server. It takes a single argument connfd, which is the file descriptor for the connection with the client.

    Inside the function:

    buff is an array used to store the messages.
    n is an integer used as an index.
    The function enters an infinite loop to continuously receive and send messages.
    bzero() is used to clear the buffer buff before reading the message from the client.
    The read() function is used to read the message sent by the client from the connection socket (connfd) and store it in the buffer buff.
    The received message is then printed.
    The buffer buff is cleared again using bzero().
    n is set to 0.
    The server message is read from the standard input using getchar() and copied into the buffer buff.
    The server message is then sent to the client using the write() function.
    If the message contains "exit", the server prints an exit message and breaks the loop to end the chat.
    
## The main : 

    This is the main() function, which is the entry point of the program.

    It declares variables sockfd and connfd for the socket file descriptors, and len for the length of the client structure.
    servaddr is a structure of type sockaddr_in, representing the server address.
    cli is a structure of type sockaddr_in, representing the client address.

    Inside the function:

    The socket is created using the socket() function, with the address domain AF_INET, socket type SOCK_STREAM, and protocol 0.
    If the socket creation fails, an error message is printed, and the program exits.
    The server address structure servaddr is cleared using bzero().
    The server address is set using the sin_family field as AF_INET, sin_addr.s_addr field as htonl(INADDR_ANY) (which represents any available local IP address), and sin_port field as the specified PORT value.
    The socket is bound to the server address using the bind() function. If the binding fails, an error message is printed, and the program exits.
    The socket is set to listen for incoming connections using the listen() function. If listening fails, an error message is printed, and the program exits.
    The length of the client address structure cli is set.
    The accept() function is called to accept an incoming connection. It blocks until a client connects to the server. If the connection acceptance fails, an error message is printed, and the program exits.
    A message is printed indicating that the server has accepted the client.
    The func() function is called to handle the communication between the client and the server, passing the connection file descriptor connfd.
    After the communication is finished, the socket is closed using the close() function.

    This program sets up a server that listens on a specified port and accepts a connection from a client. It then facilitates a chat-like interaction between the client and the server, with the server echoing back the received messages until the client sends an "exit" message to end the chat.
    
    
  ## other details : 
  
  Certainly! Let's go through the parameters of each function in the code:

    socket() function:
        Parameters:
            AF_INET: Address family, specifying IPv4.
            SOCK_STREAM: Socket type, indicating a TCP socket for stream-oriented communication.
            0: Protocol, allowing the system to choose the appropriate protocol based on the address family and socket type.
        Return value: The socket file descriptor (a non-negative integer) on success, or -1 on failure.

    bind() function:
        Parameters:
            sockfd: Socket file descriptor.
            (SA*)&servaddr: Pointer to a sockaddr structure representing the server address to bind to.
            sizeof(servaddr): Size of the server address structure.
        Return value: 0 on success, or -1 on failure.

    listen() function:
        Parameters:
            sockfd: Socket file descriptor.
            5: Backlog, indicating the maximum number of pending connections that can be queued up.
        Return value: 0 on success, or -1 on failure.

    accept() function:
        Parameters:
            sockfd: Socket file descriptor.
            (SA*)&cli: Pointer to a sockaddr structure to store the client address if the connection is accepted.
            &len: Pointer to the length of the client address structure.
        Return value: The connection file descriptor (a non-negative integer) on success, representing the established connection with the client, or -1 on failure.

    read() function:
        Parameters:
            connfd: Connection file descriptor.
            buff: Pointer to the buffer to store the received message.
            sizeof(buff): Size of the buffer.
        Return value: The number of bytes read on success, or -1 on failure.

    write() function:
        Parameters:
            connfd: Connection file descriptor.
            buff: Pointer to the buffer containing the message to send.
            sizeof(buff): Size of the buffer.
        Return value: The number of bytes written on success, or -1 on failure.

    bzero() function:
        Parameters:
            buff: Pointer to the buffer to be cleared.
            MAX or sizeof(servaddr): Size of the buffer.
        Return value: None.

    getchar() function:
        Parameters: None.
        Return value: The character read as an int.

    strncmp() function:
        Parameters:
            "exit": The first string to compare.
            buff: The second string to compare.
            4: The maximum number of characters to compare.
        Return value: 0 if the strings are equal up to the specified length, a positive value if the first differing character has a greater ASCII value, or a negative value if the first differing character has a smaller ASCII value.

    printf() function:
        Parameters:
            ...: Variable number of arguments representing the format string and optional values to print.
        Return value: The number of characters written on success, or a negative value on failure.

    close() function:
        Parameters:
            sockfd: Socket file descriptor or connection file descriptor to be closed.
        Return value: 0 on success, or -1 on failure.



