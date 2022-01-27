![Peel logo](https://wsnd.io/Vq36uXaT/peel-banner.png)
# Peel
*Peer to Peer Distributed Serverless Social Network in browser*

## Requirements
1. A modern browser (e.g. Chrome v92+, Firefox v91+, Safari v14.1+)
2. Be a nice person, in all aspects while using this webapp

**[Try it Now!](https://abemassry.github.io/peel)**

https://abemassry.github.io/peel

## Install
Peel is a mobile first webapp that can be installed to a mobile device to
appear to behave like a native app. Here are the installation instructions.
These are screenshots of iOS, Android should be very similar

Tap the share icon

![image-of-share-icon](https://wsnd.io/9zBALN80/share-button.jpeg)

Tap add to home screen

![add-to-home-screen](https://wsnd.io/Yqupnzss/install-to-homescreen.jpeg)

Tap Add in the upper right hand corner

![install-to-home-screen](https://wsnd.io/8fdsyzaW/install-screenshot.png)

It's installed!

## About
Peel is a peer to peer, distributed, serverless, social network that
operates entirely in a browser.

"Main Feed" view

![image-of-post-view](https://wsnd.io/rNIGzxfi/screenshot.png)

You can create a User

![image-of-user-create](https://wsnd.io/BTxTDb89/screenshot.png)

Make a post

![image-of-make-a-post](https://wsnd.io/RGmf2ux1/screenshot.png)


All communication is browser to browser

The main feed is persistent via Local Storage

You can also send direct messages

![image-of-dm](https://wsnd.io/lR3pOfVV/screenshot.png)

And make phone calls

![image-of-phone-call](https://wsnd.io/Swtm0VqW/screenshot.png)

Direct Messages are not persistent and not logged anywhere, they only
exist between two browsers

Phone calls are not recorded they are only an audio connection between
two browsers

## Code Layout and Style

The entire app is in one HTML file, I wanted to start small and grow from there
but like a lot of projects when I started working on it the scope blew up. So
in the future the code might be broken up into multiple files and there may or
maynot be a build process.

The CSS framework is Bootstrap, the JavaScript framework is Vanilla.js.

The project might choose a different JavaScript framework in the future.

The app in general was coded mobile first and desktop secondary.

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
* Larger scale JavaScript framework

## Supporting

If you'd like to support this project:

Sign up for an account at [I Read This Week](https://www.ireadthisweek.com)

Purchase an account at [wsend](https://wsend.net)

I also have a videogame for sale [Rain Drop](https://abemassry.itch.io/rain-drop)

As well as the soundtrack album to go with it [Rain Drop (Original Video Game
Soundtrack)](https://abemassry.bandcamp.com/album/rain-drop-original-video-game-soundtrack)

When I'm not on Peel, I'm also on Twitter
[@abemassry](https://twitter.com/abemassry), say hi sometime.
