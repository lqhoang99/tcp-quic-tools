# `QUIC` vs `TCP` performance measurement tools

### Build

Before obtaining a runnable executable file you'll have to run `go build qtm.go` to build the program.
A `main.exe` file will be created right next to the `qtm.go` file in the root of the repository.

> `qtm` is the name of the tool, which is short for **"QUIC / TCP measurement"**.

Try executing it from the command line: `qtm.exe` or `qtm` on the command line!

### Application modes

You can start the command line measurement tool in either **server** or **client** mode.
To start the tool in server mode append the flag `--server` on startup. If you omit the `--server` flag the tool is started in *client* mode by default.

##### Start tool in **client** mode
```sh
qtm
```

##### Start tool in **server** mode
```sh
qtm --server
```

### Usage

Tool syntax:
```sh
qtm <flag 1> <flag 2> ... <flag n>
```

> The flags can be in the format `-server` or `--server`


#### Connection Type

There are two connection types available:

- TCP
- QUIC

Set the connection type either if you configure nothing (The used connection type is QUIC) or if you provide the `--type` flag with the connection type. **Example:** `qtm --type=TCP`.

#### Measuring Throughput

In order to measure the throughput, you can either use:

- `--bytes` (**Example**: `qtm --bytes=10000000`) to send the set amount of bytes
- `--duration` with `--buffer-size` where you'll send for the set duration in chunks of the set buffer-size. (**Example**: `qtm --duration=5s --buffer-size=1024`)

##### TCP measuring example

Start the server with:
```sh
qtm --server --type=TCP
```

Start the client with:
```sh
qtm --type=TCP --bytes=100000000