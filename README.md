# gaia-7001a

This testnet is using a custom version of cosmos-sdk in which the sync bug from gaia-7001 is fixed.

## Setting Up a New Node

These instructions are for setting up a brand new full node from scratch. If you ran a full node on a previous testnet you will need to start from scratch due to some breaking changes in key format.

### Install Go

Install `go` by following the [official docs](https://golang.org/doc/install).
**Go 1.10+** is required for the Cosmos SDK. Remember to properly setup your `$GOPATH`, `$GOBIN`, and `$PATH` variables, for example:

```bash
mkdir -p $HOME/go/bin
echo "export GOPATH=$HOME/go" >> ~/.bash_profile
echo "export GOBIN=$GOPATH/bin" >> ~/.bash_profile
echo "export PATH=$PATH:$GOBIN" >> ~/.bash_profile
```

### Install Cosmos SDK

Next, let's install the testnet's version of the Cosmos SDK.

```bash
mkdir -p $GOPATH/src/github.com/cosmos
cd $GOPATH/src/github.com/cosmos
git clone https://github.com/cosmos/cosmos-sdk
cd cosmos-sdk && git checkout c01a3d218f2544b00b817942e996e171c397b2a4
make get_tools && make get_vendor_deps && make install
```

That will install the `gaiad` and `gaiacli` binaries. Verify that everything is OK:

```bash
$ gaiad version
0.22.0-c01a3d2
```
