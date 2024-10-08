# turbopoc

Turbocharged multichain smart contract POC template generation from the command line. This is more advanced, yet more complicated fork of great `zobront/quickpoc` tool.

## usage

From the command line, call `turbopoc [OPTIONS]... [CONTRACT-ADDRESS][:CHAIN]...`, or `turbopoc [OPTIONS]... -s https://page.to.scrap.block-explorers-addresses-from.io` to generate a ready-to-go sandbox for running POCs for the given address against multiple EVM chains, including:

- forge template with name mirroring contract name
- `src/` folder populated with all contracts and libraries
- test file autogenerated with contract import
- test setup with contract variable and mainnet forking
- graphing interaction flow, UML diagram and storage layout
- `cd folder_name` copied to clipboard to save you 1 extra second

you can run `forge test` to confirm it's working, then go into `tests/POC.t.sol` to interact with the contract (saved in storage as `c`).

## install

0) on a UNIX machine with bash installed, install all dependencies:
- foundry ([follow instructions here](https://github.com/foundry-rs/foundry))
- jq (`brew install jq`)
- graphviz (`brew install graphviz`)
- surya (`npm i -g surya`)
- sol2uml (`npm i -g sol2uml`)
- bash v4.0+

1) download the `turbopoc` file from this repo.

2) set up your block explorer API keys and RPC URL for mainnet simulation in `conf` file

3) you can then run it directly by calling the file (`./turbopoc`) 

4) more conveniently, install it globally:
- put it somewhere you won't touch it (usually `~/bin`)
- if this folder isn't already in your path, open your bash run control file (for example, `~/.zshrc`) and add the following line: `export PATH="$PATH:/Users/path_to_folder_holding_file`
- call `chmod +x path_to_file` to make the file executable
- you should then be able to call `turbopoc` from any folder to generate the POC folder within it.

## features
- support for all common EVM networks
- automatically pull all contracts listed on an immunefi (or any other) page
- automatic test generation

## troubleshooting
### unknown option: -A
Macs ship with bash v3.2 due to licensing. It was released in 2007 and lacks many modern features. This tool requires associative arrays that were introduced in v4.0. In order to fix this issue, please install most recent bash version:
`brew install bash`

This does not break anything on existing installations, as brew installs bash in user space, and /bin/bash is still default option.

## TODO
- fix issue with multiple contract having the same name
- perform best-effort merging related code into one project (depends on previous one)

please submit issues for any additional features you'd like to see :)
