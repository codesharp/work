# ZMQ notes
http://zguide.zeromq.org/page:all
http://www.dirlt.com/ZeroMQ.html
http://www.vjianke.com/ZVLJ9.clip?MobileDebug=true

* about zmq context thread safe
http://api.zeromq.org/2-2:zmq-init

* about poll
http://api.zeromq.org/2-1:zmq-poll

* The device connects a frontend socket to a backend socket.
http://api.zeromq.org/2-1:zmq-device
device configuration file
http://rfc.zeromq.org/spec:5

* sockopt
about ZMQ_LINGER how discard pending messges
http://api.zeromq.org/2-1:zmq-setsockopt
int zero = 0;
zmq_setsockopt (mysocket, ZMQ_LINGER, &zero, sizeof (zero));

* schedule
Fair-queued
round-route
Least-recently used (LRU) queue device

## FAQ
http://www.zeromq.org/area:faq

## sourcecode
https://github.com/zeromq
https://github.com/imatix/zguide/blob/master/examples/C%2B%2B/zhelpers.hpp

## usage&&sample
http://zguide.zeromq.org/c:asyncsrv
http://www.zeromq.org/blog:multithreaded-server

rpc router broker

http://zguide.zeromq.org/page:all#A-Request-Reply-Message-Broker

ROUTER-DEALER Frames 
Identity 
Reply address
mama/papa envelope(信封) [ [address|empty|data] | [address|empty|data] ]
[address3|address2|address1|empty|data]
[socket_id3|socket_id2|socket_id1|empty|data]
http://zguide.zeromq.org/page:all#Request-Reply-Envelopes

ROUTER ZMQ_XREP
DEALER ZMQ_XREQ
routing patterns:
- Router-to-dealer. [address|data] 
router.bind(addr) dealer.bind(addr)
router.connect(addr) <-queuedevice-> dealer.bind(addr)
- Router-to-mama (REQ). [address|empty|data] router.bind(addr) mama.connect(addr)
- Router-to-papa (REP). [address3|address2|address1|empty|data] router.bind(addr) papa.connect(addr)
http://zguide.zeromq.org/page:all#Custom-Request-Reply-Routing
Broker
router-device(round-trip)-dealer
router-device(LRU Queue)-router
http://zguide.zeromq.org/page:all#A-Request-Reply-Broker

PPP:Paranoid Pirate Protocol
http://rfc.zeromq.org/spec:6

MDP:Majordomo Protocol
http://rfc.zeromq.org/spec:7
http://zguide.zeromq.org/page:all#Service-Oriented-Reliable-Queuing-Majordomo-Pattern
python implementation
http://guidog.github.com/pyzmq-mdp/

FLP:Freelance Protocol
N-to-N brokerless
http://rfc.zeromq.org/spec:10


Brokerless
http://zguide.zeromq.org/page:all#Brokerless-Reliability-Freelance-Pattern
Broker vs. Brokerless
http://www.zeromq.org/whitepapers:brokerless

clusters
http://zguide.zeromq.org/page:all#Scaling-to-Multiple-Clusters

http://zguide.zeromq.org/page:all#Prototyping-the-Local-and-Cloud-Flows

Reliable RPC via retry
client retry:Use zmq_poll to do a safe request-reply
http://zguide.zeromq.org/page:all#Chapter-Four-Reliable-Request-Reply
Disconnected
http://zguide.zeromq.org/page:all#Disconnected-Reliability-Titanic-Pattern
high-availability server pair, using the Binary Star pattern 
http://zguide.zeromq.org/page:all#Clone-Server-Reliability
client retry
broker&worker heartbeat
http://zguide.zeromq.org/page:all#Robust-Reliable-Queuing-Paranoid-Pirate-Pattern

####Freelance Protocol
enable an N-to-N network of clients and servers, connected to each other 
in peer-to-peer fashion
brokerless
multi-threaded server
enable server failover and recovery
Clients MAY send ping commands at regular intervals. A client SHOULD consider a server "disconnected" if no "pong" arrives within some multiple of that interval (usually 2-3).
用于实现点对点rpc，耗时调用
http://rfc.zeromq.org/spec:10


heartbeating
You might be tempted to open a separate socket dialog for heartbeats. 
This is superficially nice because you can separate different dialogs, e.g. the synchronous request-reply from the asynchronous heartbeating. 
####However it's a bad idea for several reasons. 
First, if you're sending data you don't need to send heartbeats. 
Second, sockets may, due to network vagaries, become jammed. 
You need to know when your main data socket is silent because it's dead, rather than just not busy, so you need heartbeats on that socket. 
Lastly, two sockets is more complex than one.
http://zguide.zeromq.org/page:all#Heartbeating

pair Primary|Backup|Master|Slave 
http://zguide.zeromq.org/page:all#Detailed-Requirements

http://www.slideshare.net/randybias/distributed-rpc-in-nova-with-zeromq
http://readthedocs.org/docs/pycon-2012-notes/en/latest/dotcloud_zerorpc.html

## bindings
http://nzmq.codeplex.com/

## same as
http://msgpack.org/

## other
So we do a little calculation and see that this will work nicely over plain TCP. 2,500 clients x 10/second x 1,000 bytes x 2 directions = 50MB/sec or 400Mb/sec, not a problem for a 1Gb network.
ZMQ sends and receives them atomically
zmq queue and zookeeper?
nsf Brokerless mode
nsf CenterBroker mode
nsf rpc模式选型 MDP FLP PPP
client retry?如何判断connect timeout？poll timeout 耗时调用超时如何判断？
broker-worker heartbeat for queue crash/restart or workder failure

## perf
* local=win7 x86 2core
* remote=win2008 x86 4core
* workers=2-4
- rpc(request&reply) perf test with keeped socket
	- inproc perf 400000calls/s
	- local tcp perf 2000-3000calls/s
	- remote tcp perf  800-1000calls/s
- rpc(request&reply) perf test without keeped socket
	- local tcp perf 100-200calls/s
	- remote tcp perf  100calls/s
- rpc(request&reply) perf test without keeped connect
	- local tcp perf 500+calls/s
	- remote tcp perf  300+calls/s
- rpc(request&reply) local router test
	- local tcp perf 2000-3000calls/s
	- remote tcp perf 800-1000calls/s
- rpc(request&reply) remote router test
	- local tcp perf 1000calls/s


	
	
test client req-rep rep down
test broker router-router down
test server req down

