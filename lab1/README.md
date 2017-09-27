# Lab 1
## Remember `TCP`?

### Keywords
`tcp`, `udp`, `client`, `server`, `ip`, `http`, `proxy`

### Objective
Get to remember (or learn and understand) what you did at the `Programarea în Rețea` course:
- build `TCP` and `UDP` server/client "programs" using [sockets](http://en.wikipedia.org/wiki/Bsd_sockets);
- get an [`HTTP`](http://en.wikipedia.org/wiki/HTTP) page (read [RFC 2616](https://tools.ietf.org/html/rfc2616));
- have fun (probably).

The tasks given here are meant to guide you through the wonderful world of network programming.

Examples of how you might run your script are shown after every task.

1. send `UDP` or/and `TCP` messages (**required**) `[1]`<br> You'll get `1` point if you are able to send and receive `UDP` and `TCP` messages, but you can implement just one type of socket and explain what are the differences in implementing the other type and how would you implement it.
```shell
# by default it might send TCP packets
$ myscript.py -t 192.168.0.10 -p 12345 -m "blabla"
# or, by adding another flag: -u it will send an UDP packet
$ myscript.py -t 192.168.0.10 -p 12345 -m "blabla" -u
# or by adding the -l (listen) flag it makes it a
# server that accepts and prints connections
$ myscript.py -t 192.168.0.10 -p 12345 -l
```
  1.1 send a message at fixed intervals (every 5s send something, with the possibility to indicate the *maximum* number of messages) `[0.5]`
  ```shell
  # -i might indicate the time interval
  # and -max the number of messages
  $ myscript.py -t 192.168.0.10 -p 12345 -m "blabla" -i 1 -max 10
  ```
2. port scanning of a given `IP` (with possibility of including a range of ports; ex: 1-100) `[1]` <br> Also, you could get `1` point for  this without implementing the task, if you would explain how this could be implemented and in what use-cases might it be useful to check if certain ports are open on a server.
```shell
# -s (scan) could indicate the port(s) to scan
$ myscript.py -t "mysite.com" -s 1-100
```
3. get a page over http `[0.5]` <br> Guess what: you get full points on this if you explain how you would request (`get`) a page from a host; explain why using `https` on your servers is more secure.
```shell
$ myscript.py -t "mysite.com" -get
```
4. listen on an `ip:port` and redirect messages to another `ip:port` (simple proxy) `[1]` <br> The point here is to understand the point of a proxy, and further down the line, we might get to implement our own that might help hide our trace on the network.
```shell
# use -rt (for redirect target) and -rp (for redirect port)
$ myscript.py -t 192.168.0.10 -p 12345 -rt 192.168.0.11 -rp 12345
```
5. send file over a network `[1]`
```shell
# use -f (file) to indicate the location (global or relative) of your file
$ myscript.py -t 192.168.0.10 -p 12345 -f "file.txt"
```
6. add the possibility to use either the full description (a *verbose* output of the program) of what the script does, or the minimal amount of info to understand that the task has been completed `[1]` <br> An example would be when you are probing the ports of a host: the *verbose* output should show every port that has been tried (even if it refused the connection) and the *non-verbose* one would only show the ports that are open.

If you think that it might be easier to write separate scripts for each task, then do so.

### Grading policy
**8** - implement `1` point worth of tasks <br>
**9** - implement `2` points worth of tasks <br>
**10** - implement `3+` points worth of tasks (the extra points will go to the next labs, if you'll need them)

> **Note** <br>
> The following examples are written in `Python`, but they are purely educational and it does not imply that you should use `Python` to implement this or the following laboratory works.

### Examples
### `TCP` Server
```python
import socket


# ip and port that will be used to create the server
# '127.0.0.1' would do the same thing
IP = 'localhost'
PORT = 12344

#initialize the socket with default settings
tcp_server = socket.socket()

#bind the socket to an interface
tcp_server.bind((IP, PORT))
print('bind successful')
#make it listen
tcp_server.listen(5)

print('server is listening')

#accept an incoming connection
client_socket, addr = tcp_server.accept()

#display some data about the connected client
print('connection from:', addr)

#receive a message (1024 bytes) from the client
message = client_socket.recv(1024)
print(message.decode())

#send a message to the client
client_socket.send('message received'.encode())

#close everything
client_socket.close()
tcp_server.close()
```

### `TCP` Client *(counterpart)*
```python
import socket


# ip and port that will be used to create the server
# '127.0.0.1' would do the same thing
IP = 'localhost'
PORT = 12344

#initialize the socket with default settings
client_socket = socket.socket()

#connect to the server
client_socket.connect((IP, PORT))
print('connected successfuly')

#send a message to the client (and encode it)
client_socket.send('message'.encode())

#receive a message (1024 bytes) from the client
message = client_socket.recv(1024)
print(message.decode())

#close everything
client_socket.close()
```

