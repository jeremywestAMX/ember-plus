# Introduction #

Glow Logger Proxy is a Windows application that acts as a middleman between an Ember+ consumer and a provider by forwarding traffic received from either party to the other one and logging all messages into an XML log file.

Glow Logger Proxy requires the .NET Framework 4.5 and is available [here](https://drive.google.com/uc?id=0B8xV96MSXVvqUDZFYnN0b3hVWDQ&export=download).


# Details #

![http://ember-plus.googlecode.com/svn/wiki/GlowLoggerProxy.png](http://ember-plus.googlecode.com/svn/wiki/GlowLoggerProxy.png)

After pressing the **Start** button, the application basically does the following:

  1. Listen for connection requests from an Ember+ consumer on the port number entered for **Listening Port**.
  1. As soon as a connection request is made, the connection with the consumer is established.
  1. A connection is established with the provider identified by **Provider Host Name** and **Provider Port**.
  1. Any bytes received from the consumer are forwarded to the provider and vice versa.
  1. The received bytes are also fed into a logger which writes a log file to the folder entered in **Log Folder**. A new file is created for each connection.


# Feedback #

Please ask questions in the [forum](https://groups.google.com/forum/#!forum/ember-plus-discuss) and file bugs and feature requests with the [issue tracker](http://code.google.com/p/ember-plus/issues/list).