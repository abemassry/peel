![Peel logo](https://wsnd.io/Vq36uXaT/peel-banner.png)
# Peel
*Peer to Peer Distributed Serverless Social Network in browser*

## Requirements
1. A modern browser (e.g. Chrome v92+, Firefox v91+, Safari v14.1+)
2. Be a nice person, in all aspects while using this webapp

**[Try it Now!](https://abemassry.github.io/peel)**
https://abemassry.github.io/peel

## About
Peel is a peer to peer, distributed, serverless, social network that
operates entirely in a browser.

You can create a User
![image-of-user-create](link/to/user/create)

Make a post
![image-of-make-a-post](link/to/make/a/post)

And see others posts
![image-of-post-view](link/to/post/view)

All communication is browser to browser

The main feed is persistent via Local Storage

You can also send direct messages
![image-of-dm](/link/to/dm)

And make phone calls
![image-of-phone-call](/link/to/phonecall)

Direct Messages are not persistent and not logged anywhere, they only
exist between two browsers

Phone calls are not recorded they are only an audio connection between
two browsers

## The Peel Protocol

The peel network exists as a shared state in between all of the browsers
participating in the network. State is persistent via Local Storage.

The state is communicated to the other nodes in the network whenever
a change is made. One node is connected to another node and mutual
connection is possible, but it is also possible for a non mutual
connection to be made. This is how we avoid the many to many problem.
Each node can connect to a different node like a linked list and forward
the message along.

In addition one node can be a hub by adding symmetric connections,
meaning if a node already has a peer, but an additional node wants to
connect the first node adds an additional connection and it starts
acting like a hub and fans out messages to it's main connection as well
as it's symmetrical connections.

When one to one connections are possible in addition to one to many all
participating in the same network there is less of a chance of "network
islands" to appear. Meaning the app still looks like it's functioning
correctly but all participants are not connected to each other, one
group might section off. If a hub appears there is less of a likelihood
of this happening because one node can act as a bridge in this
situation.

In the discovery phase a counter is incremented and the next available
ID is tried, if successful the ID becomes the ID of that node and the
user is then associated with that ID for the lifetime of the current
browser session. Once an ID is found, IDs are then cycled to try to find
a peer participating in the same network. If a peer is found
a connection is made and the originating peer polls the connection for
any new messages.

If a new message is sent the receiver must forward the message along. In
order to avoid infinite positive feedback loops many checks are made to
determine if the message should be forwarded along.

* Who is the originator of the message?
* Who is the sender of the message?
* Should this message be fanned out to the symmetric connections?


WebRTC is the communication protocol that is used and the connections
are set up using [peerjs](https://peerjs.com/).

Once a direct message is requested since the node IDs have been shared
with all members participating in the network a direct message can be
sent to a peer. Upon sending a direct message an additional WebRTC
connection is made between the two browsers and a phone call can be
initiated by either browser over WebRTC.

## Future Work

The future tasks are listed in the ToDo section of the project page for this
repo [ToDos](https://github.com/abemassry/peel/projects/1)

Longer term goals include:
* Video Calls
* Peer to Peer binary transfer
* Choosing what kind a feed to see based on a follower mechanism
* Address Book or Recently Contacted list
* Native App that participates in the WebRTC network
* Video Broadcasting

## Supporting

If you'd like to support this project:

Sign up for an account at [I Read This Week](https://www.ireadthisweek.com)

Purchase an account at [wsend](https://wsend.net)

I also have a videogame for sale [Rain Drop](https://abemassry.itch.io/rain-drop)

As well as the soundtrack album to go with it [Rain Drop (Original Video Game
Soundtrack)](https://abemassry.bandcamp.com/album/rain-drop-original-video-game-soundtrack)

When I'm not on Peel, I'm also on Twitter
[@abemassry](https://twitter.com/abemassry) say hi sometime.
