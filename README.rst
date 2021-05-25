Hypark
######

WIP: Simple Client-Server Networking Library

Note: This project will be developed mainly for academic purposes. There are
plenty of open source networking clients and servers in the Python ecosystem for
you to choose if you neeed any ;D.


Introduction
============

Hypark is a networking library that abstracts away the retrieval and delivery
of data messages for Python applications. In the server, it implements the
**ASGI** specification to provide both request/response and streaming
capabilities. In the client, it emulates as much as possible the server
interface to provide a symmetric development experience.


Usage
=====

To start a new **server** and begin to process new connections, just
provide an **ASGI application** asynchronous callable to **serve**:

.. code::

   import asyncio
   from hypark import serve

   class Application:
       async def __call__(self, scope, receive, send):
           """Handle new client connections"""


   app, config = Application(), {'port': 8080}
   asyncio.run(serve(app, config))


Features
========

Hypark is expected to be minimal. Its applications are supposed to be run
behind a reverse proxy such as nginx or apache, which will be the responsible
of establishing network security and load balancing capabilities. Hypark uses
*Sans I/O* application protocol libraries to provide the semantics of the 
messages it receives and sends. In general, Hypark supports:

- Single server socket listening
- Unencrypted network connections
- HTTP/1.1 message processing
- ASGI server conformance 
- Symmetric Server/Client User API 
