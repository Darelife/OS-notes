[[CV's and Semaphores]]
# IPC Mechanisms

1. Unix Domain Sockets
2. Message Queues
3. Pipes
4. Shared Memory: threads, and libs
5. Signal: basically an intr

## Message Queues

Internal linked list within the kernels addressing space basically. Messages can be sent to the queue in order and retrieved from the queue in several different ways.

Each message queue is uniquely identified by an IPC identifier. Open connection a message queue identified by a "key" get a handle. Sender opens connection to message queue, and sends the message. Receiver opens connection to the message queue, and retrieves the message later on.

Message buffered within message queue / mailbox until retrieved by receiver

`msgget()` : to create the message queue
`msgsend()` : to send the message in the queue
`msgrcv()` : to receive the message
`msgctl()` : to delete the message queue

Active Queues in the kernel : ipcs -q

## Shared Memory

In Message Queues, Pipes, Sockets, we basically have to copy the data from the sender process address space to the kernel address space, and then, from it to the reader process address space.

In shared memory, both processes can access the memory directly, making it the faster form of IPC.

The shared memory segment is mapped to the address space of both processes. As soon as the first process writes data in the shared memory segment, it becomes available to the second process.

Active Shared Memory segments : ipcs -m

[[File System]]