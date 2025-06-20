
# AIMPyfly

An AIM client class library for Python. The library currently facilitates connecting to the AIM service, sending and receiving instant messages, and provides the groundwork for further/future functionality.

## Features

- **Connect to AIM servers**: The client allows users to authenticate and establish a connection to AIM servers.
- **Send/Receive Instant Messages**: The client can send and receive messages to/from other AIM users in real time.

## Getting Started

### Installing

`pip install aimpyfly`

### Example: Connecting, Sending, and Receiving Messages

This script demonstrates how to connect to the AIM server, log in with your credentials, send a message to another user, and receive incoming messages. 

```python
import asyncio
import logging
from aimpyfly import aim_client

# Define a callback for handling incoming messages
async def message_received(sender, message):
    print(f"New message received from {sender}: {message}")

async def main():
    # Initialize the AIM client with your credentials and server details
    client = aim_client.AIMClient(server="<server>", port=5190, username="<screenname>", password="<password>", loglevel=logging.<LEVEL>)

    # Set the callback to handle incoming messages
    client.set_message_callback(message_received)

    # Connect to the AIM server
    await client.connect()

    # Send a message to another AIM user
    await client.send_message("ukozi", "Hello! This message was sent using the AIM Python client.")

    # Keep the client running to handle and process incoming messages
    await client.process_incoming_packets()

if __name__ == "__main__":
    asyncio.run(main())
```

**What This Does:**
- Connects to the AIM server using your provided server, username, and password.
- Sends a message to a specific AIM username (\`ukozi\`).
- Listens for incoming messages and prints them when received.
- The client will keep running, allowing real-time message exchanges with other AIM users.

### Current Work in Progress

I'm actively working on extending this client to support additional features:
 - Join and interact with AIM chatrooms
 - Viewing user profiles
 - Setting the profile of python client
 - Viewing away messages
 - Setting the away message of the python client
 - Selecting client type.

I encourage contributions to help build out this functionality!

### Logging

The code includes detailed logging, which can be useful for debugging and understanding the network communication between the client and the AIM servers. Log messages include information about sent and received FLAP and SNAC packets. To set logging verbosity, pass `loglevel=logging.<LEVEL>` when creating an instance of AIMClient.

### Acknowledgments

Special thanks to:

- [**Retro AIM Server**](https://github.com/mk6i/retro-aim-server)
- [**Aleksandr Shutko (iserverd)**](https://ox.github.io/iserverd-oscar-mirror/)
- [**Adam Fritzler (libfaim)**](https://sobek.hsdn.org/Docs/oscar/Oscar%20Protocol%20Specification/)
- [**Paul Swartz (Twisted Matrix)**](https://web.archive.org/web/20110412050057/http://twistedmatrix.com/trac/wiki/TwistedWords)

### Contributing

If you'd like to submit your own improvements:

1. Fork the repository.
2. Create a new branch for your feature (\`git checkout -b feature/new-feature\`).
3. Commit your changes (\`git commit -m 'Add new feature'\`).
4. Push to your branch (\`git push origin feature/new-feature\`).
5. Open a pull request for review.

### License

This project is licensed under the MIT License.
