<!--
## Installing from PPA

```shell
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```

If you want to stay on the bleeding edge, install the `ethereum-unstable` package instead.

After installing, run `gdex account new` to create an account on your node.

You should now be able to run `gdex` and connect to the network.

Make sure to check the different options and commands with `gdex --help`

You can alternatively install only the `gdex` CLI with `apt-get install gdex` if you don't want to install the other utilities (`bootnode`, `evm`, `disasm`, `rlpdump`, `ethtest`).
-->
## Building from source

### Building Gdex (command line client)

Clone the repository to a directory of your choosing:

```shell
git clone https://github.com/dexon-foundation/dexon
```
Install latest distribution of Go (v1.10) if you don't have it already:

[See instructions](https://github.com/dexon-foundation/wiki/wiki/Installing-Go#ubuntu)

Building `gdex` requires Go and C compilers to be installed:

```shell
sudo apt-get install -y build-essential golang
```

Finally, build the `gdex` program using the following command.
```shell
cd dexon
make gdex
```

You can now run `build/bin/gdex` to start your node.