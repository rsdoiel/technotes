
# Network Protocals

The internet is a network of networks.  Today we take this for granted.  In the past it was
a challenge.

The successful network communication between computers is governed by [protocols](http://en.wikipedia.org/wiki/Internet_Protocol). In this article I am introducing
a few specific protocols that collectively are known as IP or Internet Protocols. It is
background for future technotes.


## What is a protocol?

A protocol is an agreed upon manner of interacting between two entities (e.g. a web browser
talking to a webserver). Before computers protocols referred to the rules of interaction in
political bodies (e.g. a royal court) and between nations. It also has been used in medicine
to describe the procedure to diagnosis and treat an illness.

Today the term finds itself tied to computers and computer networks.  In that context I am
using this definition--

	A protocol is the agreed upon method of exchanging information 
	between computers.


### Why is this important?

If your vocation involves the Web your vocation is made possible because of protocols.  I
will use a building analogy to imply its importance. A foundation is required by what you
build on top of it. It provides the platform and stability to work. Importantly what you put
on top is what most people notice (e.g. house, office building, park). This deminishes the
appearence of importance.

If a building rests on a broken foundation it will become structurally compromised. Similarly
if you build a building without respecting its foundation it can be structurally compromised.
Understanding the foundation helps you build and avoid compromise. On the web humans interact
with webpages.  They think of the web through the lense of pages and web applications. But what
those stand on it a set of protocols.  Abusing the protocols will cause problemsfor the website,
application or web browser.


### Are protocols for computers complicated?

Yes and no, there are allot of specific details but the concepts are straight forward.
Let me explore human protocols first. When humans communicate verbally we form sounds into
words, words into phrases, phrases into sentences. Generally one person speaks then another.
Sometimes two people speak at the same time.  Most of the time the conversation will still be
understood by both parties. We also can let the other person know when something was confusing
or spoke over.  That processs is a verbal information protocol. 

Let me illustrate what the protocol view of a conversation.

1. I having an idea
2. My brain translates the idea into a sequence of words
3. I speak them and wait for a response
4. You hearing sounds 
5. You process those sounds into a sequence of words
6. You interpret the sequence into a meaningful idea(s)
7. You think of another idea to response
8. Your brain translates the idea into a sequence of words
9. You speak the words
10. I hear the sounds
11. I process those sounds into a sequence of words
12. I interpret the sequence into a meanful idea(s)

Steps 1 through 12 describe a protocol (a set of expected steps to communicate).
It also relies on other protocols - the organization of sounds into words we both understand.

With human protocol we can be a bit fuzzy.  A Californian English accent is largely understandable
by someone from New York. Allot of fuzziness can be resolved through context.  With 
computers we need to be very specific because computers and the network hardware 
they rely on are very literal and tolerate ambiguity poorly. That is why protocols appear
complicated. Fuzziness is replaced by explicit detail.

Protocols can stack one on top of anther, be used in parallel and used exclusively depending on their
nature.  In computer technology we see protocols evolve. We use version numbers to identify
expectations (e.g. HTTP 1, HTTP/2).  Often a lower level protocol (e.g. forming a sequence of 
sounds into a words) is abstracted by higher level protocols (e.g. using words to form sentences,
sentence to form paragraphs).  

On the Web our protocols are built on Internet Protocols which are built on lower level network
protocols eventually drilling down to the specific sequence of bits and bytes the hardware expects.


# Important protocols, January 2015

Below is a shortlist of protocols used today by the Internet and Web.
In semi-historical order--

+ Part one
	+ TCP/IP and UDP/IP
	+ FTP and Telnet
	+ HTTP
+ Part Two
	+ SSL/TLS
	+ SFTP, SSH and HTTPS
	+ SPDY
	+ HTTP/2
	+ DTLS/SRPT and WebRTC


## TCP/IP and UDP/IP

TCP/IP is a grandfather protocol and pre-dates the Internet and Web.  
It was created to allow computer networks to communicate among themselves.  In 
the late 1960s there were many types of network. Most were proprietry and only communicated 
with like networks. Inevitably these networks needed to be bridged together. The need was driven by 
the desire to share hardware resources and data. DARPA, a coldwar era federal agency, was
charged with antipating threats and planning responses commissioned research in this area. 
One focus was responding to a war tactic of disrupting and destroying ememy command and 
control infrastructure.  DARPA funded ARPANET as a means of researching solutions to this 
problem.  TCP/IP comes from ARPANET which is the parent of the Internet and
grandparent of the Web.


TCP stands for _Transmission Control Protocol_.  But what is it? 

TCP defines the basic elements used to successfully communicate between computers 
over an IP network. Software referred to as the TCP/IP stack breaks down the content 
into smaller chunks which in turn are assembled packets and data grams. These packets
travel through the network (over wire, fiber or wireless spectrum) then get assembled
again at the other end. This contents transmitted include the data the computer is trying 
send as well as additional information about the final destination.  

An important feature of TCP is that is manages to keep those packets ordered even 
when some paths across the network might be conguested or unresponsive. This 
means if I type "Hello World" into a chat program at work chatting with my 
friend in another place it still comes out "Hello World" on the otherside and 
not "WorldHe llo".

TCP was optimized for sending streams of information, usually text, between computers. 
TCP enabling building tools for interactive communications between computers.

Another important grandfather protocol is UDP - User Datagram Protocol.  It dates 
from the 1980s. It is used when TCP is considered too heavey to be practical.  UDP 
achieves this slimming down by dropping some of the guarantees that TCP insists on. 
This includes assertions about order and confirmation about successful transmission. UDP 
is particularly useful when delay in communications is more harmful than a missed or 
corrupted delivery.  Many _real time_ protocols build on UDP. An example would be 
voice communications.


### FTP and Telnet

Sending TCP or UDP data packets between computers is not an end in itself.  People want to do things with
computers.  Two protocols built on top of TCP/IP are FTP and Telnet.  Before the Web 
and Internet moving data from computer site to another often involved copying information to tape and 
physically sending the tape to another location (e.g. via the Post office). When computing sites started 
being networked an early use case was sending data files from one system to another over the network.  
The need to making it easier to consistently send, receive and manage files across different computers
spawned the creation of FTP - File Transfer Protocl. The Unix command that provided a means to use the
protocol also bares the same name. Likewise accessing and controlling a remote computer over a TCP/IP
spawned Telnet which refers to both a protocol and Unix command.

When FTP and Telnet were first created they were used on closed networks. As a result the primary risk of
compromised assumed physical access to the network hardware or computers on that network. All transactions
using either protocol were visible in plain text.  When the Internet arrived the assumption of a 
friendly network changed.


## HTTP

HTTP stands for Hypertext Transfer Protocol. It coordinates the transmition of text, 
images, and even video across networks. It is used by servers who store and distribute content 
as well as web browser and mobile applications that receive the content. It is the enabling 
protocol of the Web. HTTP protocol supports a few _verbs_ for interacting with content.  Unlike
FTP that content does not have to be a file. It could the output of a program (e.g. a web service)
but often it is a file. Along with a few verbs HTTP also supports metadata about the item being
requested or sent. This metadata includes things like size, file type. It can also include things like
authorization tokens, browser state (e.g. cookies).  It is quiet flexible.  The common verbs of HTTP 
are GET, POST, PUT, DELETE, HEAD. Each services a purpose. One of the clever applications of these 
verbs is REST - Representational State Transfer which allows a database like mapping of actions - 
create, read, update and delete by mapping to POST, GET, PUT and DELETE along with other metadata provided
in the HTTP Header.

HTTP is an asyncronous protocol unlike Telnet.  By clever use of the HTTP Headers we can build a interaction
which is syncronous and this experience is what we see in web applications like GMail or buying something at Amazon.

When the Web started supporting more sensitive transctions revealed a problem (e.g. transporting private communications, on-line purchases). Like FTP and Telnet before it all the transaction over the network
took place in plain text and could be eavesdroped very easily.


## Some context

There are several imporant influences on the net when Tim Berners-Lee dreams up the world wide web in CERN.

1. The Internet expanded from a few institutions to a global collection of networks and systems (there were Internet accessible sites in America, Europe and Asia).
2. The Internet shifted from part-time connection to full-time connections (e.g. creation and decline in usage of [UUCP](http://en.wikipedia.org/wiki/UUCP))
3. The interactive Internet move beyond plain text to more immersive content including images, diagrams eventually video.
4. With faster full time connctions new human organizations were possible (e.g. software development models moved from isolate shops who exchanges tapes to the open model assumed by Linus Torvolds and the spread of Linux)
5. The Web increased the number of participants and decreated the barriers to participation.

No. 5 is important. The assumed trust did not prove reliable. Mischief changed from traditional April 1st jokes to more serious things.


## Some implications

* When you convert binary content into text the data being transfer tends to grow larger. This lead to optional use of compression in webservers.
* Content changes at different rates. HTTP Headers have evolved to help manage/take advantage of the difference.
* HTTP was created as a asynchronous protocol but humans like systems that are synchronous, HTTP Headers have been used to help create context between asynchronous requests.
* [Ajax techniques](ihttp://en.wikipedia.org/wiki/Ajax_(programming)) are limited by basic fundimentals of TCP/IP and HTTP it is "heavy" in the same way that TCP/IP is "heavy" compared to UDP/IP. New protocols and APIs like WebSockets have evolved to replace Ajax transactions.
* A web page today is likely more than one document
	* Each (sub)document goes through a request process (even if it is only a header exchange) 
	* Each document request eats up network connections and take time. 
	* A major challenge today is wrangle the web page such that there is a balance in the number of requets, size of documents and round trip connection time need to assemble the final view.
* In 1989 you were lucky to find 100 people looking at your website, today it is reasonable to assume you have suppport thousands and even tens of thousands of symultaneious requests. 

The explosion in web traffic can be framed by what is called the [C10K](http://www.kegel.com/c10k.html) 
problem. The term was coined by Dan Kregal in 1999. Even in 2015 I find it challenging to get my 
colleagues to appreciate the implications of this when building websites. 

Part of the C10K problem is hidden by how we view the web today. We view the web through the lense of webpages.
Humans tend to view a webpage as one document because that is how we experience it. That turns out to rarely be the 
case today.  A poorly designed webpage can range turn into a request for hundreds of documents. This easier to see 
when you consider that a webpage often has many image files, CSS files (describing layout), JavaScript files 
(containing behaviors). The latter two can in turn request more files. Send this down a slow or conguested 
network (Edge, like 3G, 4G, 4G LTE) and you a very unpleasant and frustratine experience.


## SSL, TLS, SFTP and SSH

So FTP, Telnet and HTTP started out as clear text protocols with a problem of eavesdropping. How do we address
that? We create some more protocols.  When humans communication over a distance in written form
and want to prevent eavesdropping they can write their messages in code. That is also what we can do with
computer protocols. The specifics for how you wrap your clear text in encryption is addressed by the SSL protocol.

SSL stands for secure sockets layer.  The basic idea is to combine encryption the information before it is broken 
into TCP/IP or UDP/IP packets. Since FTP, Telnet and HTTP are build on TCP/IP and SSL privides a mechanism for 
wrapping those protocols in encryption. This allows us to make a secure FTP now called SFTP, a safer HTTP called 
HTTPS. Telenet itself was superceded by SSH which provided a secure means of accomplishing the same goals.

Unfortunately SSL proved to be breakable. It has largely been replaced by 
[TLS](http://en.wikipedia.org/wiki/Transport_Layer_Security) - Transport Layer Security. If you are talking with 
someone about computer security they tend to be specific about the transport security layer and they will make a 
distinction between SSL and TLS. If you are talking with someone causally often people will say SSL when they really
mean TLS. To muddy waters further there are programming libraries that use SSL in their method names when they 
actually implement TLS. The bottom line is you want to use TLS. It is the standard today for encrypting the 
channels of communicaiton. One of Fall 2014 big security issues was that many websites and services had not
upgraded to TLS support.  Do to the high profile compromises many organizations had to scramble to switch all
their systems and services to use the newer more secure TLS.

Evergreen versions of most web browsers, SFTP, SSH and HTTPS today uses TLS. 


### Implications of encrypted services

When HTTPS was first introduced it is required more processing power from the machines running the webserver. Many 
websites would only resort to using it if they had to.  Today that is not as much of a problem. Many website use a 
load balancer and they provide direct hardware support for TLS.  Also most computers, even your phone, have multple 
cores (processors) that make easier work of encrypting and decrypting messages.  If you are setting up a website 
today it is better to setup with HTTPS support and redirect all traffic to it if you can.  It still inflicts some 
headache for the developer and system admin but generally that is a reasonable price of business.

The enscryption model supported by TLS uses [Public Key 
Encryption](http://en.wikipedia.org/wiki/Public-key_cryptography) to keep things safe. This means there are files 
called a public key and private key that need to be generated and managed appropriately. The keys are also referred 
to as certificates and credentials. TLS like SSL before it trys to make sure that the end points you are 
communicating with are who they say they are. This is done by an exchange of public keys and signing the delivered 
content. If the host key does not match (or cannot be verified by an approved certificate authority) the
transaction can be blocked or terminated. You see this most commonly when you access a developer machine where the
developer is using a "self signed" certificate.  Getting your web browser to accept the certificate can either mean 
diving into the internals of your browser preferences or using a known certificate issued by a known authority. If 
you use a certificate authority they normally charge you money for the certificate hence developers self sign.


## What the heck is [SPDY](http://en.wikipedia.org/wiki/SPDY)?

A few years ago Google Inc. realized that HTTP/HTTPS traffic used allot of bandwidth in relationship to the content 
they were delivering. They wanted to improve the situation (it would save them money).  Like UDP/IP in relationship 
to TCP/IP they realized much of the HTTP transaction was not needed. The result of their research was SPDY. SPDY, a 
name tradmarked by Google, is an open protocol designed to augment HTTP and HTTPS.  Currently SPDY is at version 3. 
Evergreen versions of Firefox, Chrome, Opera, Safari and IE all support it. It has formed a test bed for our next 
generation of HTTP. Most popular webservers (e.g. Apache, NginX) now can support SPDY version 3. It does require
installation and configuration of the SPDY modules.  Once setup ongoing management of SPDY support is generally 
limited to intervention when versions change. 

For the users of the Web SPDY provides for better fit at the protocol layer for various types of content delivery 
or service interacitons. For the service providers it means a lower number of bytes transmitted and potentially 
more effecient resource usage on the server.


## HTTP/2

As content usage and applications on the web have changed the original HTTP protocol is beginning to be long in the tooth.  With the success of alternatives like SPDY the web server and browser makers are getting ready for an update. Over the next year we are likely to see its support and adoption. [HTTP/2](http://en.wikipedia.org/wiki/HTTP/2) which as a draft specification in 2014 is moving through the RFC process in 2015. In the meantime we can get ready for the transition by taking advantage of SPDY version 3.1.


## DTLS, SRTP and [WebRTC](http://www.webrtc.org/)

One dream on the web has been for an easy way to send a link and have working per to per connection for things like text, audio and video chat.  This capability has been formalized in an API called WebRTC and related protocols [DTLS](http://en.wikipedia.org/wiki/Datagram_Transport_Layer_Security) and [SRTP](http://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol).  TDLS seeks to secure the packet layer effeciently and SRTP to proctect the content
layer and prevent playing back the content in appropraitely.

WebRTC project goes back to 2011 with support added in the development branches of the major browsers in 2014. With 2015 [WebRTC](http://caniuse.com/#feat=rtcpeerconnection) support is landing in stable branches of browsers for both desktop and mobile.

WebRTC makes it easy to 

+ provide realtime audio and video per to per communication (e.g. bypass WebEx)
+ direct per to per messaging rather than going through a services like Facebook, Google, Apple or your phone company
+ data transfer including text messaging and shared document editing
+ look for sensor networks adopting WebRTC support for [IoT](http://en.wikipedia.org/wiki/Internet_of_Things), Internet of Things, applications.

Mozilla implemented a JavaScript library for multi-user text editing using WebRTC last year. Google demoed per to per video conferencing in 2011 when the project became public.  There are JavaScript libraries that can be used to polyfil browsers during the transition to full support.

Except clever things to be done with WebRTC as the year progresses.


