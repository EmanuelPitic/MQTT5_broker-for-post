# MQTT5 Broker

This project implements a simple MQTT5 broker that manages client connections, authentication, and session persistence through an SQL server for storing client data. The code is structured into multiple modules, each with specific functionalities for decoding and creating MQTT packets, as well as managing connections and authentication.

## Project Structure

### Main Files

- **`server.py`**: The main module that implements the MQTT5 server. Manages client connections, client interactions, and database communication.
  - [Detailed explanation for `server.py`](Docs/server.md)

- **`gui.py`**: The graphical interface for the MQTT broker. Allows starting and stopping the server, as well as monitoring connections, messages, and other relevant information.
  - [Detailed explanation for `gui.py`](Docs/gui.md)

- **`sqlServer.py`**: The module that manages database-related operations, including authentication, storage, and updating of client information in the SQLite database.
  - [Detailed explanation for `sqlServer.py`](Docs/sqlServer.md)

- **`decoder.py`**: Implements the `MQTTDecoder` class, which is used for decoding MQTT packets received from clients, such as `CONNECT`, `PINGREQ`, and `DISCONNECT`.
  - [Detailed explanation for `decoder.py`](Docs/decoder.md)

- **`packet_creator.py`**: Contains the necessary functions for creating MQTT packets, such as `CONNACK`, `PINGRESP`, and `DISCONNECT`, which are sent as responses to clients.
  - [Detailed explanation for `packet_creator.py`](Docs/packet_creator.md)

## Requirements

- Python 3.x
- `socket` library (included natively in Python)
- `struct` library (included natively in Python)
- `PyQt5` library for the graphical interface

## Server Configuration

The server is configured to run on IP address `127.0.0.1` (localhost) and port `5000`. These values can be modified in the `server.py` file.

## Usage

1. **Starting the Server**:
   To start the MQTT5 Broker server using the graphical interface, run the command:
```bash
   python gui.py
```
   From the graphical interface, press the **Start Server** button to initialize the server.

2. **Monitoring Connections and Messages**:
   - **Topic History Tab**: Displays the history of topics used.
   - **Last 10 Messages Tab**: Shows the last 10 messages published on a selected topic.
   - **Connected Clients Tab**: Lists connected clients and their subscriptions.
   - **Subscribed Clients Tab**: Presents subscribed clients for each topic.
   - **QoS 1/2 Messages Tab**: Displays messages published with QoS 1 and 2.

3. **Stopping the Server**:
   From the graphical interface, press the **Stop Server** button to stop the server.

## Module Details

### server.py

`server.py` is the main module that manages client connections, client authentication, and MQTT packet processing using `decoder.py` and `packet_creator.py`. More information can be found in the [documentation for `server.py`](Docs/server.md).

### gui.py

`gui.py` implements the broker's graphical interface, allowing the server to be started and stopped, as well as viewing and managing data in an intuitive way. For more details, access the [documentation for `gui.py`](Docs/gui.md).

### sqlServer.py

`sqlServer.py` defines the `SQLServer` class for database interaction. This module manages authentication and maintains information about clients, including the time of last disconnection. Detailed documentation can be found [here](Docs/sqlServer.md).

### decoder.py

`decoder.py` implements the `MQTTDecoder` class for decoding MQTT packets. It interprets received packets of type `CONNECT`, `PINGREQ`, and `DISCONNECT`. For a detailed explanation, visit the [`decoder.py` documentation](Docs/decoder.md).

### packet_creator.py

`packet_creator.py` contains the necessary functions for creating MQTT packets, including:
- **`create_connack_packet`**: Creates a `CONNACK` packet to confirm connection with the client.
- **`create_pingresp_packet`**: Creates a `PINGRESP` packet to keep the session active.
- **`create_disconnect_packet`**: Creates a `DISCONNECT` packet to inform the client that it has been disconnected.

More details can be found in the [`packet_creator.py` documentation](Docs/packet_creator.md).
