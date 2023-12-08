# Running the Everywhere Computer✵
Welcome 👋!

The Everywhere Computer✵ is powered by [homestar](https://github.com/ipvm-wg/homestar) nodes — a reference implementation of the [IPVM](https://github.com/ipvm-wg) protocol. These exercises will help you:
1. **Setup** a homestar node on your local machine 
2. **Run** workflows locally 
3. **Share** computation across a p2p network

For full documentation, please see https://docs.everywhere.computer/. If you get stuck at any point, please follow the Discord link from https://control.everywhere.computer and ask the community for help.
## Preparation
We’ve said that computation on the Everywhere Computer✵ is both portable and durable. These two traits are, in part, made possible thanks to the power of [IPFS’ content addressing](https://fission.codes/blog/content-addressing-what-it-is-and-how-it-works/), and web assembly’s ability to execute in just about *any* environment — including browsers.
### 1. Install IPFS
Just as the Everywhere Computer✵ is powered by homestar, IPFS is powered by kubo — the GoLang IPFS node. You have two options for installing it: 
1. Install the kubo binary directly: https://docs.ipfs.tech/install/command-line/#install-official-binary-distributions 
2. or, install IPFS Desktop GUI which includes kubo: https://docs.ipfs.tech/install/ipfs-desktop/
### 2. Run IPFS
Make sure kubo is running! Either by launching IPFS Desktop, or running `ipfs daemon` in your terminal.  
### 3. Add some web assembly functions  
Now that IPFS is running on your machine, we can add our initial web assembly functions to it. All functions on the Everywhere Computer✵ are [content addressed](https://fission.codes/blog/content-addressing-what-it-is-and-how-it-works/) on IPFS, which means they are identified and located using something call a CID (Content IDentifier).

To add the functions to your local IPFS node, run:
```
ipfs add --cid-version 1 ./functions.wasm  
```
## Installing homestar  
To install your first Everywhere Computer✵ homestar node, we recommend downloading a build directly from github. 

🚧 This is still under very active development! 🚧
### macOS  
Install homestar using brew by running:  
```
brew install fission-codes/fission/homestar  
```
### Linux  
1. Go to this page and scroll down to "Artifacts": https://github.com/ipvm-wg/homestar/actions/runs/7117766904
2. Download the `.zip` file for your platform - we recommend the `musl` build for linux
3. Unzip the file and move the `homestar` binary to somewhere in your path (e.g. `/usr/local/bin`)  
4. Make sure the binary is executable (`chmod +x /usr/local/bin/homestar`)
### Windows  
Using WSL2 is recommended for this workshop. If you're using Windows, please follow the Linux instructions above.  

## Booting up the Everywhere Computer✵
One final thing: we'll want to generate a key for your homestar node. This will be used to identify your node on the Everywhere Computer✵ network. To do this, run:  
```
openssl ecparam -genkey -name secp256k1 -outform DER -out secp256k1_key.der  
```

We can now start the node by running:  
```
homestar start -c ./settings.toml  
```

It's alive!

## Running the control panel  
Visit https://control.everywhere.computer/. With both your `homestar` and IPFS nodes running locally, you can experiment with creating your own workflows and running them locally.
