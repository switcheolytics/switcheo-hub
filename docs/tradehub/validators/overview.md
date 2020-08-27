> Validators provide the critical tasks of confirming blocks and securing the network.

## Installation

Switcheo has provided excellent documentation on this topic on their [GitHub](https://github.com/Switcheo/tradehub/blob/master/README.md).

The commands to assist validators can be found at [helpful commands](commands.md)


## Validator keys

Protecting a validator's consensus key is the **most important** factor to consider when designing your setup. The key that a validator is given upon creation of the node is called a consensus key, it has to be online at all times in order to vote on blocks. It is not recommended to merely hold your private key in the default json file (priv_validator_key.json).

Currently Tendermint uses Ed25519 keys which are widely supported across the security sector and HSMs.

Backing up this file is the most important part of the validators role. Switcheo has provided their guidelines on how to setup a KMS to ensure this file is not compromised: https://github.com/Switcheo/tradehub/blob/master/KMS.md

## Monitoring

This is a work in progress but will be similar to the options available from Cosmos.

<!-- ## Automatic Claiming for your Delegators

This is a work in progress and code will be available shortly. -->

## Automation

The steps required to automate this setup are currently being worked on and this section will be updated when complete.