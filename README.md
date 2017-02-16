#####################################################################
#				Back Challenge								#
#					Skylar Labs										#
#####################################################################


#Task#

The goal of this challenge is to build a chat system, using python, Django, with or without Redis to build a Long Polling Chat System.

The goal is to not use WebSockets but long polling to retrieve messages after posting a message, ask the server for response, and wait,
until the server reply, or stop the listening after a period of time, and ask again.

That's opposite to the regular fetching where, you set an interval of time and the client fetch new messages, that can easily overload the
server if thousands of clients are asking for a resource each 10s and there's no new data, that will be a lost of request and an useless
response from server.

With Long Polling, client ask for a resource, wait for a period of time until server reply, if server replies, it consumes the data.  
If there's no data within the period of time, the client close the connection, and ask again and wait again, and so on.

With that system, we can go from 6 requests per minute to 2-3 requests per minute, which mean the server's load is cut by half.

#Tools#

	Server
	-  Python
	-  Django
	-  Redis [Optional](1)
	Client
	-  HTML/Javascript

#Tests#

To test the system, a server and 2 clients talking to each others can be used.
Initial States:
Client 1 and Client 2 listen to server
Working States:
Client 1 send message to Client 2
Client 1 wait for answer from Client 2
Client 2 receives message, reply, and listen to server(answer from Client 1)
Client 1 receives message from Client 2, reply and listen to server(answer from Client 2)
And so on and so on


#Resources#
[Long Polling](https://www.pubnub.com/blog/2014-12-01-http-long-polling/)  
(1) Redis can be used for its Sub/Pub feature.
