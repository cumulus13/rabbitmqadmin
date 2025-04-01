# RabbitMQ Admin Tool

`rabbitmqadmin.py` is a command-line tool for managing RabbitMQ servers via the HTTP API. It provides functionality to list, show, declare, delete, close, purge, import, export, publish, and retrieve RabbitMQ objects and messages.

## Features

- **Object Management**: Declare, delete, and manage RabbitMQ objects such as exchanges, queues, bindings, vhosts, users, permissions, parameters, policies, and more.
- **Data Export/Import**: Export and import RabbitMQ definitions for backup or migration purposes.
- **Message Handling**: Publish messages to exchanges and retrieve messages from queues.
- **Customizable Output**: Supports multiple output formats, including table, JSON, TSV, and key-value pairs.
- **SSL Support**: Secure connections using SSL with options for certificates and hostname verification.
- **Configuration File**: Use a configuration file to simplify repeated connections to RabbitMQ servers.

## Requirements

- Python 2.6+ (Python 2.7.9+ is required for HTTPS support).
- RabbitMQ Management Plugin enabled on the RabbitMQ server.

## Installation

1. Clone or download this repository.
2. Ensure Python is installed on your system.
3. Install any required dependencies (e.g., `ctraceback`, `pydebugger`, `configset`).

## Usage

Run the script with the desired subcommand and options:

```bash
python rabbitmqadmin.py [options] subcommand
```

### Subcommands

#### Display Commands
- `list <object>`: List RabbitMQ objects (e.g., queues, exchanges).
- `show <object>`: Show detailed information about RabbitMQ objects.

#### Object Manipulation
- `declare <object>`: Declare a new RabbitMQ object.
- `delete <object>`: Delete an existing RabbitMQ object.
- `close <connection>`: Close a RabbitMQ connection.
- `purge <queue>`: Purge all messages from a queue.

#### Broker Definitions
- `export <file>`: Export RabbitMQ definitions to a file.
- `import <file>`: Import RabbitMQ definitions from a file.

#### Publishing and Consuming
- `publish`: Publish a message to an exchange.
- `get`: Retrieve messages from a queue.

#### Help
- `help subcommands`: List all available subcommands.
- `help config`: Display help for the configuration file.

### Options

- `-H, --host`: RabbitMQ server hostname (default: `localhost`).
- `-P, --port`: RabbitMQ server port (default: `15672`).
- `-u, --username`: Username for authentication (default: `root`).
- `-p, --password`: Password for authentication (default: `root`).
- `-V, --vhost`: Virtual host to connect to (default: `/`).
- `-s, --ssl`: Enable SSL for secure connections.
- `--ssl-key-file`: Path to the SSL key file.
- `--ssl-cert-file`: Path to the SSL certificate file.
- `--ssl-ca-cert-file`: Path to the CA certificate file.
- `-f, --format`: Output format (e.g., `table`, `pretty_json`, `tsv`).
- `-t, --request-timeout`: HTTP request timeout in seconds (default: `120`).

### Configuration File

You can use a configuration file to simplify repeated connections. The default configuration file path is `~/.rabbitmqadmin.conf` or `rabbitmqadmin.ini`.

Example configuration file:

for `rabbitmqadmin.conf`
```ini
[default]
hostname = localhost
port = 15672
username = guest
password = guest
vhost = /
ssl = False
```

for `rabbitmqadmin.ini`
```ini
[auth]
username = root
password = root
hostname = 192.168.100.2
port = 
```

for `rabbitmqadmin.conf`, specify the configuration file can be using the `-c` or `--config` option.

## Examples

### List Queues

```bash
python rabbitmqadmin.py list queues
```

### Declare a Queue

```bash
python rabbitmqadmin.py declare queue name=my_queue durable=true
```

### Publish a Message

```bash
echo "Hello, RabbitMQ!" | python rabbitmqadmin.py publish routing_key=my_queue payload_encoding=string
```

### Export Definitions

```bash
python rabbitmqadmin.py export definitions.json
```

### Import Definitions

```bash
python rabbitmqadmin.py import definitions.json
```

## Bash Completion

The script includes support for bash completion. To enable it, generate the completion script and source it:

```bash
python rabbitmqadmin.py --bash-completion > rabbitmqadmin_completion.sh
source rabbitmqadmin_completion.sh
```

## License

This project is licensed under the MIT License, See the file for details.

## Acknowledgments

- Developed by cumulus13.
- Contributions and feedback are welcome!

## editor
[Hadi Cahyadi](mailto:cumulus13@gmail.com)
    

[![Buy Me a Coffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/cumulus13)

[![Donate via Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/cumulus13)
 
 [Support me on Patreon](https://www.patreon.com/cumulus13)