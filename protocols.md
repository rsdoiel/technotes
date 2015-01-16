
# Protocals

## An internet history lesson through exploring protocols

The internet is a network of networks.  It is important that
the computers can communicate reliably among themselves as well as 
across external networks. Today we take this for granted.  In the past
it was a challenge.

The successful communication between computers are governed by
[protocols](http://en.wikipedia.org/wiki/Internet_Protocol) or more formally
internet protocols...


## What is a protocol?

A protocol is an agreed upon manner of transaction (e.g. communicaition)
between two entities.  Before computers protocols referred to the rules
of interaction in political bodies (e.g. a royal court) and between nations.

Today that term finds itself tied to computers and specifically to computer 
networks.  For the purposes of this document I am using
this definition--

	A protocol is the agreed upon method of exchanging information 
	between computers.


## Why is this important?

If your vocation involves the world wide web your is made possible because of protocols.
Protocols are the foundation block. If your web browser is analogous to a car then
the protocols are the road. More more accurately how the road should be constructed
and function so that you can safely drive your car among other cars.  If you are building 
on the web (either code or content) you can leverage your basic understanding of 
protocols to avoid problems down the road.

Another way of looking at it is using a building analogy. The foundation is the protocol
what you put on top if it is what most poeple notice (e.g. house, office building, park).
If a building rests beyond its foundation or has a broken foundation it will become
structurally compromised. 

Willful ingornance of internet and web protocols by those who build on the web raises 
the risks of structual compromise of our websites and applications. Compromise can hurt others.


## Import protocols January 2015

Below is a shortlist of protocols used today in the workings of internet, websites 
and applications. This list is in semi-historical order.

+ tcp/ip and udp/ip
+ ftp and telnet
+ http
+ ssl, sftp and ssh
+ http/https 1
+ spdy
+ http/https 2
+ webrtc


### TCP/IP and UDP/IP

TCP/IP is a grandfather protocol for the internet and dates back before the world wide web.  It was created to allow computer networks to communicate amamonth themselvse.  As networking took off in the late 1970s there were many types of network and all were exclusive to themselves for the most part. Inevitably these networks needed to be bridged together so they could share resources, code, data and plain old text communications. Enter DARPA. Confronting the threat of gobal nuclear war was a priority of defense researchers from WWII through recent decades.  One primise was that a nuclear holicost would have survivers and there for would need to re-group and keep things going.  A basic war tactict is to destroy the ememy command and control structures and this mean both audio/visual communication and in the 1970s increasingly computer communications.  The U.S. Federal Government through DARPA funded the creation of a network of networks which could survive breakage and disruption.  This resulted in a research network called DARPA Net and that became in internet.

The TCP protocol formed the foundation of the early internet and remains critical today.  TCP stands for Tramission Control Protocol. When humans communication verbally we form sounds into words, words into pharses, phrases into sentenses, etc.  Sometimes two people speak at the same times often overlapping.  Most of the time the conversation will still be understood by both parties and normally we have social convension to help us avoid confusing overlap.  TCP defines the basic elements used to successfully communication with other computers who also known TCP. Software in the computers breaks what the human wants to send down into data grams. These are sent across the network of networks to the destination and then are re-assembled at the other end. An important feature of TCP is that is manages to keep those packets ordered even when some paths across the network might be conguested or unresponsive. This means if I type "Hello World" into a chat program at work chatting with my friend in another place it still comes out "Hello World" on the otherside.

TCP was optimized for send streams of information, often textual, between computers. It supports interactive communications.  It along with UDP is the foundation other internet and web protocols are often built on. These includeHTTP/HTTPS (web protocol), SMTP/POP3/IMP (email protocols), and SSH/SFTP.

ANother important grandfather protocol is UDP - User Datagram Protocol.  It dates from the 1980s. It is used when TCP is considered to "heavey weight" to be practical.  UDP achieves this slimming down by having few guarantees about order and successful transmission. It is particularly useful when delay in communications is more harmful than delivery and order.  Many "real time" protocols build on UDP.  An example would be early voice communications, event log streaming. Like TCP UDP is built on by other protocols.

Both are important to web in that they provide the foundation to build on.

### FTP and TELNET

Before the world wide web one and before the internet moving data from computer system in one site to another often involved copying information to tap and physically send the tap to another location (e.g. via the Post office). When computing sites started being network together an early usecase was sending data from one system to anther.  By the seconds there was a common concept for organizing data. It was called a file. A file was analogous to your paper file you might find in a filing cabinet at your place of business. When DARPA network was create different methods were used to moving these files between systems.  Eventually it became desirable to replicate the filing cabinet as well as the file concept. The trouble was differing computer systems interally organized things very differently. With the popularity of the Unix style filesystems a common approach was created and the protocol describing how to map that organization was also create - FTP - File Transfer Protocol.  FTP allowed one computer network to present a common file system to antoher computer network and coordinate the delivery and management of file between them.

Besides accessing files often times users of one computer system would want to access and run process on another system on the work. Again various approaches were taken but eventually Telnet protocol was evolved to allow for interactive control. This was particilarly advantaguous with the arrival of time sharing system (i.e. multi-user computer systems).  

By the time DARPAnet was evolving into the Internet the problem of eavesdropping had reared its head. Both FTP and Telnet communicated between computers using plain text.  If you could access the network hardware or memory on the receiving computer you could watch what was exchanged and make a copy of it easily. This was like party lines in the early telephone system.  There needed to be a more secure way for these systems to communicate and that lead to - SSL, SFTP and SSH.

It is important to note that the world wide web was invented before the more secure forms existed.  The world wide web leveraged TCL/IP and sat between FTP (a file system view of content) and Telnet (an interactive view of a computer system).  Like Telnet and FTP the first version of the web protocol, HTTP, transfered data "in the clear" meaning anyone could internet it.

## HTTP

HTTP stands for Hypertext Transfer Protocol. It coordinates the transmition of text, images, and even video across networks. It is used by servers who store and distribute content as well as web browser and mobile applications that receive the content. It is the enabling protocol of the world wide web.

In its original form transmission was in text format only. If you had an image or other binary file you wanted to transfer you encoded into text. To let the receiving system know how to interpet the document a preamble called an _HTTP Header_ was attached to the encoded text. Likewise the requesting system (e.g web browser) used HTTP Headers to tell the content system what types of formats it can read.  Over timeHTTP header elements have grown facilitating a high level of control over HTTP communications.


## A pause for context

There are several imporant influences on the net when Tim Berners-Lee dreams up the world wide web in CERN.

1) The internet has expanded from a few institutions to a global collection of networks and systems (there are internet accessible sites in America, Europe and Asia).
2) The internet has shifted from part-time connection to full-time connections (see the story of UUCP - Unix to Unix communication protocol)
3) The interactive internet started straining to move beyond plain text to more immersive content including images, diagrams eventually video.
4) With faster and full time connctions new human organizations were possible (e.g. a change of software development models from restrictive and tap exchange based to the open model assumed by Linus Torvolds and the spread of Linux)
5) With the arrival of the web the number of participants and the barriers to entry dropped.

#5 is important. The assumed trust did not prove reliable. Mischief changed from traditional April 1st jokes to things more serious. Before DARPANet it often was necessary to gain physical access to a system to compromise it. By the arrival of the internet that was not the case.


## A pause for implications

* When you convert binary content into text the data being transfer tends to grow larger. This lead to compression (strinking the text back down) binary content transfer support.  
* Some content changes frequently other rarely. HTTP Headers have evolved to help manage the difference
* HTTP was created as a asynchronous protocol but humans like systems that are synchronous (i.e. context it carried between transactions), HTTP Headers have been used to help create context between asynchronous requests
* [Ajax techniques](ihttp://en.wikipedia.org/wiki/Ajax_(programming)) are limited by basic fundimentals of TCP/IP and HTTP
* HTTP Headers can also become large so alternative protocols are evolving to manage that
* A web page today is likely more than one document
	* Each (sub)document goes through a request process (even if it is only a header exchange) 
	* Each document request eats up network connections and take time. 
	* A major challenge today is wrangle the web page such that there is a balance in the number of requets, size of documents and round trip connection time need to assemble the final view.
* In 1989 you were lucky to find 100 people looking at your website, today it is reasonable to assume you have suppport tens of thousands of symultaneious requests. This known as the [C10K](http://www.kegel.com/c10k.html) problem. The term was coined by Dan Kregal in 1999. Even in 2015 I find it challenging to get my colleagues to appreciate the implications of this when building websites. 

Part of the C10K problem is hidden by how we view the web today. We view the web through the lense of webpages. Humans tend to view a webpage is one document because that is how we experience it. That turns out to rarely be the case today.  A poorly designed webpage can range turn into a request for hundreds of documents. This easier to see when you consider that a webpage often has many image files, CSS files (describing layout), JavaScript files (containing behaviors). The latter two can in turn may request more files. Send this all down a slow and conguested celluar data network and you a very unpleasnt experience both sides of the connection for humans and computers.


## SSL, TLS, SFTP and SSH

Headlines today show us that information can be weaponized.  Say you are looking at recipes for dinner. Also assume I know you last visited the grocery store a week ago.  If you linger I can bet you are concidering the prepration this gives me the inuition that 1) you will go to the grocery store or call for delivery and 2) you will prepare some food. Depending the recipe I might beable to determine if you are cooking for one or a whole crowd (e.g. Christmas Goose).  If I wish to burgle your house I can make plans.Moral never look at recipes :-).

That example is contrived to make the point. Something socially safe as food can be used to tell me something about you personally. That makes the world a little creepy. Maybe there is a safer way to move about on the internet and web.

Commonly (at least since Greek/Roman times) keeping messages safe in transit has involved cyphers and codes. You take your message and encrypt it so it is secret and the recepient on the other end decrypts it so they understand the contents.  Computers were actually developed to break these codes - [Blechtey Park](http://www.bletchleypark.org.uk/) is famous for this. Naturally computers and networks can take advantage of encryption and that leads to the next batch of protols.

SSL stands for secure sockets layer.  The basic idea is to combine encryption with a protocol like TCP/IP. Use TCP/IP to make sure your data gets to here you want and encrypt inside of that data so the content is hard to reveal. Someone who can monitor the network traffic can see where the encrypted packets come from and where they go but would have to break the encryption (something that is possible given sufficient time and computation resources) to know what is inside. Three portocols we introduced earlier were improved by this - FTP became SFTP, Telnet was replaced by SSH and HTTP gained a brother called HTTPS.

The trouble of encryption is that it can be broken. SSL proved to be breakable and has largely been replaced by [TLS](http://en.wikipedia.org/wiki/Transport_Layer_Security) - Transport Layer Security. If you are talking with someone about computer security they tend to bea specific meaning and will say TLS. If you are talking with someone causally often people will say SSL when they really mean TLS. To muddy the waters some there are programming libraries that use SSL in their method names when they actually implement TLS. The bottom line is you want to use TLS. It is the standard today for encrypting the channels of communicaiton.

Current versions of SFTP, SSH and HTTPS today uses TLS. SFTP is our friendly file transfer protocol and is still used to move files between systems. There is also command called _scp_ which stands for secure copy and it can be executed from the command line of most Unix systems (e.g. Terminal on a Mac). SSH
has replaced Telnet. SSH stands for secure shell. It provides a means of controlling another computer interactively in a "shell" session. If you are familiar with a Mac the Terminal App launches a shell. The experience is similar but your working on a remote computer.  Today most web developers and web designers are expected to be comfortable working at the shell level and familar with both the _ssh_ and _scp_ Unix commands.  You can actually do allot more with _SSH_ than just terminal work but I will leave that for another article.  Finally we have HTTPS - this is the TLS wrapped version of HTTP. It allows us to communicate with webservers in a safer fashion (e.g. I can use my credit card at Amazon).

### Implications of encrypted services

When HTTPS was first introduced is required more processing power from the machines running the webserver. Many websites would only resort to using it if they had to.  Today that is not as much of a problem. Many website use a load balancer and they provide direct hardware support for TLS.  Also most computers, even your phone, have multple cores (processors) that make easier work of encrypting and decrypting messages.  If you are setting up a website today it is better to setup with HTTPS support and redirect all traffic to it if you can.  It still have some headache for the developer and system admin though.  The scryption model supported by TLS uses [Public Key Encryption](http://en.wikipedia.org/wiki/Public-key_cryptography) to keep things safe. This means there are documents called a public key and private key have to be generated and managed appropriately. This documents usually referred to as certificates are the key to keeping things safe.  Additionally TLS like SSL before it trys to make sure that the end points you are communicating with are who they say they are. This is done by an exchange of public keys and "signing" the delivered content. If the host key does not match (or cannot be verified by an approved certificate authority) the transaction can be blocked or terminated. You see this most commonly when you access a developer machine where the developer is using a "self signed" certificate.  Getting your web browser to accept the certificate can either mean diving into the internals of your browser preferences or using a known certificate authority's generated certificate.  If you use a certificate authority they normally charge you money for the certificate hence the self signed certs developers use.

## What the heck is [SPDY](http://en.wikipedia.org/wiki/SPDY)?

A few years ago Google Inc. realized that HTTP/HTTPS traffic used allot of bandwidth. Allot of this was probably not necessary given the evolution of what was sent and received over the net.  They wanted to iprome this situation (it would save them cache and resources) and they proposed SPDY. SPDY is a name tradmarked by Google though they have evolving the protocol as an open standard.  Currently SPDY is at version 3. Firefox, Chrome, Opera, Safari and IE all support it. It has formed a test bed for our next protocol. SPDY is not so much a replacement for HTTP but an extension of it.

## HTTP 2

As content usage and applications on the web have changed the original HTTP protocol is beginning to be long in the tooth.  With the success of alternatives like SPDY the web server and browser makers are getting ready for an update. Over the next few years we will see a shift in support and adoption. There is precidence for this. SSH went through a version 1 to 2 transition a few years back.  If we are building new web servers and services we should support SPDY version 3.1 today and plan to support [HTTP/2](http://en.wikipedia.org/wiki/HTTP/2) as RFC process moves on.


## [WebRTC](http://www.webrtc.org/)

One dream on the web has been for an easy way to send a link and have working per to per connections for things like text, audio and video connections.  This has been formalized in WebRTC which is a web protocol for real time communicatins without the requirement of plugins or server software. It works in a per-to-per fashion. With this you can use Chrome browser on one device, send a link a a Firefox users and have a video chat, or jointly type a document. Again _this happens without the need for a server component or some sort of plugin_. My guess is this will change the web significantly clever applications arrive.

WebRTC project goes back to 2011 with support added in the development branches of the major browsers in 2014. With 2015 [WebRTC](http://caniuse.com/#feat=rtcpeerconnection) support is landing in stable branches of browsers for both desktop and mobile.

WebRTC makes it easy to 

+ send text messages without going through the phone company, Google or Facebook chat services
+ it support per to per real time audio and video
+ data share files per to per
+ Mozilla implemented a JavaScript library for multi-user text editing using WebRTC last year.

Except clever things to be done with WebRTC as the year progresses.


