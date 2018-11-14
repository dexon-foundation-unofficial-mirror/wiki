<!--
## Installing with Homebrew

By far the easiest way to install wiki is to use our
Homebrew tap. If you don't have Homebrew, [install it first](http://brew.sh).

Then run the following commands to add the tap and install `gdex`:

```shell
brew tap dexon-foundation/dexon
brew install dexon
```

You can install the develop branch by running `--devel`:

```shell
brew install dexon --devel
```

After installing, run `gdex account new` to create an account on your node.

You should now be able to run `gdex` and connect to the network.

Make sure to check the different options and commands with `gdex --help`

For options and patches, see: https://github.com/dexon-foundation/homebrew-dexon
-->

## Building from source

If you don't have Homebrew, [install it first](http://brew.sh).

### Building Gdex (command line client)

Clone the repository to a directory of your choosing:

```shell
git clone https://github.com/dexon-foundation/dexon
```

Building `gdex` requires the Go compiler:

```shell
brew install go
```

Finally, build the `gdex` program using the following command.
```shell
cd dexon
make gdex
```

If you see some errors related to header files of Mac OS system library, install XCode Command Line Tools, and try again.

```shell
xcode-select --install
```

You can now run `build/bin/gdex` to start your node.