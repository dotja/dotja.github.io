---
layout: post
date: 2020-01-22
summary: "A look into the difference between sockets and ports as well as some python code."
content_description: "Sockets and Ports are 2 different things. Explore basic sockets and ports for developers. Provide examples using Python"
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Sockets and Ports</span></h1>
    <small>22 Jan 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>With</kbd> DevOps being more common these days, programmers with systems knowledge have more leverage. In this article we will take a closer look at sockets and ports.
</p>

<p id="blog_text">
A socket enables 2 processes to communicate with each other. Communication can be in the form of sending a message, sending a file, a request over a network or other.
</p>

<p id="blog_text">
When 2 processes are on the same host they can establish channel-like communication. A socket (termed Unix socket in this case) is first created then it is bound to a file (named or unnamed) on the host's filesystem in which both processes have access to.
</p>

<p id="blog_text">
If the 2 processes are on different machines, each process needs to identify itself by providing the IP address of the machine it is running on in addition to the port number where the process is reserved to run. An Internet socket, in this case, has the job of locating applications on the Internet thereby requiring the support of protocols such as TCP. On an IP address and port number combination, a server would be listening for incoming messages from several clients each having their own sockets.
The port - which is part of the Internet socket, helps redirect the packets arriving at the machine to the right application.
</p>

<p id="blog_text">
When creating a socket, you need to specify 2 arguments.
The first is domain, which describes the purpose of the socket. For example, AF_UNIX is used when the 2 processes are bound to the same machine. In case processes are on different machines, AF_INET is used. AF_VSOCK is another example and it is used to allow communication between virtual machines and their hosts.
The second argument is type and it describes the logic in which the data between the processes is transferred. Here we will consider SOCK_STREAM which is a 2-way reliable transmission. The type of the socket can have several protocols associated with it and 1 protocol may be chosen.
</p>

<p id="blog_text">
Creating and running a socket involves system calls. System calls are executed in the Kernel on behalf of the user. The Python code below makes use of these system calls under the hood.
For a server/client scenario, let's see what the code looks like in Python.
</p>

<pre>
## server code
import socket as s
def server():
    ## create the server socket
    ss = s.socket(s.AF_INET, s.SOCK_STREAM)
    server_addr = ('localhost', 12345)
    try:
        ## bind the socket to an IP and port
        ss.bind(server_addr)
        ## start listening on that socket
        ss.listen(1)
        ## accept incoming requests
        conxn, addr = ss.accept()
        print("Accepted connection from: " + str(addr))
        while True:
            ## receive data from the client
            data = conxn.recv(1024).decode()
            if data:
                print("This is what the client sent: " + str(data))
    except:
        conxn.close()

if __name__ == '__main__':
    server()
</pre>

<pre>
## client code
import socket as s
class client:
    def __init__(self):
        ## create the client socket
        self.cs = s.socket(s.AF_INET, s.SOCK_STREAM)
        server_addr = ('localhost', 12345)
        ## connect to the running server we created
        self.cs.connect(server_addr)
        self.msg_elems = []
    def send_msg(self):
    """ A method to send user input to the server """
        msg = input('->')
        self.cs.send(msg.encode())
        self.msg_elems = msg.split()
    def start_chat(self):
    """ A method to send send messages to the server
    until the user types bye """
        while 'bye' not in self.msg_elems:
            self.send_msg()
        self.cs.close()

if __name__ == '__main__':
    cl = client()
    cl.start_chat()
</pre>

<pre>
## run the server code
$ python server.py 
Accepted connection from: ('127.0.0.1', 61811)
This is what the client sent: hi
This is what the client sent: how are you
This is what the client sent: ok bye


## run the client in another session and interact with the server
$ python client.py 
->hi
->how are you
->ok bye
</pre>
</div>