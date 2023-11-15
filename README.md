# IPVM Homestar Workshop - Istanbul, 2023

Welcome to the workshop! 👋

We are going to be getting up and running with [homestar](https://github.com/ipvm-wg/homestar), the [IPVM](https://github.com/ipvm-wg) reference impelementation. We'll be running workflows locally and seeing how homestar works across the p2p network.

For full documentation on homestar, please see [https://docs.everywhere.computer/](https://docs.everywhere.computer/).

## Preparation

### Install dependencies

Please ensure you have the following tools installed and available: `git`, `node` and `kubo`:

- Install git: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
- Install node (`v18.0.0` or newer): https://nodejs.org/en/download
- Install kubo: https://docs.ipfs.tech/install/command-line/ (or desktop: https://docs.ipfs.tech/install/ipfs-desktop/)

### Run kubo

Make sure kubo is running! Either by launching IPFS Desktop, or running `ipfs daemon`.

### Add web assembly functions

All functions (along with inputs and receipts) are content addressed. We will refer to them by their CID. To add the functions to your local IPFS node, run:

```sh
ipfs add --cid-version 1 ./functions.wasm
```

## Installing Homestar

To install homestar for this workshop, we recommend downloading a build directly from github. (this is still under very active development!)

### macOS

Install homestar using brew by running:

```sh
brew install fission-codes/fission/homestar
```

### Linux

1. Go to [this page](https://github.com/ipvm-wg/homestar/actions/runs/6855172583) and scroll down to "Artifacts".
2. Download the `.zip` file for your platform - we recommend the `musl` build for linux
3. Unzip the file and move the `homestar` binary to somewhere in your path (e.g. `/usr/local/bin`)
4. Make sure the binary is executable (`chmod +x /usr/local/bin/homestar`)

### Windows

Using WSL2 is recommended for this workshop. If you're using Windows, please follow the Linux instructions above.

## Starting your homestar node

We'll want to generate a key for your homestar instance. This will be used to identify your node on the network. To do this, run:

```sh
openssl ecparam -genkey -name secp256k1 -outform DER -out secp256k1_key.der
```

We can now start the node by running:

```sh
homestar start -c ./settings.toml
```

## Running the control panel

We can now run the control panel to see our node in action. To do this:

Clone the control panel repo:

```sh
git clone https://github.com/fission-codes/everywhere-computer-control-panel.git
```

Install the dependencies:

```sh
cd everywhere-computer-control-panel
npm install
```

Run the app:

```sh
npm run start
```

Now you should be able to open the control panel at [localhost:4173](http://localhost:4173)
