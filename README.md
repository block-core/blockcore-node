# Blockcore Node

Reference implementation of Blockcore based blockchain.

## Build your own blockchain

So you want to build your own blockchain? Then you have come to the right place.

This repository is all you need to get started building your own blockchain based on the Blockcore Platform.

## Fork the repository

Start by clicking the Fork button on the top of the repository on GitHub. After you have your own fork, clone your own repository to your local computer.

## Generate your own genesis block

All blockchains start with a genesis block. This is the starting point that all other blocks build upon.

(TODO: Build a binary release of the generator to make step simpler)

To generate your own genesis block, you can use our [Blockcore Genesis Block Generator](https://github.com/block-core/blockcore-tools/tree/master/src/Blockcore.Generator).

All you need is a unique text sentence used to seed your genesis block.

For Bitcoin, this is:

```
The Times 03/Jan/2009 Chancellor on brink of second bailout for banks
```

You must make it something unique and special for your own blockchain. Reference to an historical event is a good idea, as that defines a certain epoc when your blockchain was made.

Example (Windows):

```
Blockcore.Generator.exe "My Unique Blockchain"
```

It is going to take a while to mine this block, the application is using software based Proof-of-Stake mining to find the correct hash that has enough difficulty.

When the application is done, it writes a file named "genesis.txt" in the same folder as you ran the application from. Take a backup of this file, you will need the details from it when you move to the next step. Note that there are no secrets in this file, you don't need to hide it.

## Configure your own node

Blockchains runs on full node software. Whenever you read about "node" in the context of Blockcore, it is usually a full node that does full validation of the blockchain.

First step is to install our public available Blockchain template for the dotnet new command.

If you don't have .NET Core SDK installed on your computer yet, download it from here: https://dotnet.microsoft.com/download

Make sure you get the .NET Core SDK 3.1 (not .NET Framework).

After installation, open a command prompt and navigate to the src folder in your local cloned fork.

Then run the following command:

```
dotnet new -i Blockcore.Coin.Template
```

Open the [src\SETUP.bat](src\SETUP.bat) (Windows) in your favorite text editor and start editing all the configuration settings available.

If you are on Linux or Mac, you can copy the content of SETUP.bat and put in a shell script file, or you can manually execute the CLI command with all the parameters.

### References for setup values

cointype: https://github.com/satoshilabs/slips/blob/master/slip-0044.md

pubkeyaddress, scriptaddress, secretaddress: https://en.bitcoin.it/wiki/List_of_address_prefixes

## Generate your node code

After updating all settings in the SETUP.bat file, you can now run it to generate your own custom blockchain node.

```
src\SETUP.bat
```

This will generate a new folder named the same as your output configuration in setup file. Inside this folder you will find the source code for your node.

Open the solution file in Visual Studio 2019 and run the .Node project.

You have now successfully made your own custom blockchain.

## Next steps

There are many additional things you'd want to do, to complete your own custom blockchain. You can run your chain without DNS nodes, but that means you need to hard-code all your nodes with IP addresses.

To learn more about your custom DNS nodes, check out: TBD

You can fork one of the multiple user interfaces built with Blockcore compatibility, including the "Blockcore UI" (basic wallet), "Blockcore Core" (cold-staking wallet) and the "Blockcore Hub" (extended functionality).

To gain insight to your blocks, you'd want to fork the [Blockcore Indexer](https://github.com/block-core/blockcore-indexer) and [Blockcore Explorer](https://github.com/block-core/blockcore-explorer) so you have an explorer that allows you to search and look up blocks, transactions and addresses.

Additional insight to your chain can be provided using the [Blockore Insight](https://github.com/block-core/blockcore-insight).
