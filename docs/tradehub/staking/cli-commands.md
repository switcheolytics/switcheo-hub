> Backing up your mnemonic is CRITICAL for safety of your funds. Please consider safe measures to backup and store your credentials.

> Most of this documentation is from trial and error or reference from the gaiacli from the Cosmos project.

## Keyring

When creating or restoring a wallet a local keyring is created at `~/.switcheocli/keyring` and this password is used to unlock the keyring when private keys are required for signing transations. It is possible to create or import multiple wallets into your keystore as long as they have unique names. But you will always use the same password to access these keys.

* **Long Passwords** - there appears to be an issue with passwords that are longer than 50 characters as the keyring does not allow the keyring to be unlocked and will continually state invalid password even with the correct password entered.
* **Security** - this password needs to be unique and include as many combinations of cases, numbers, and characters. If this file is divulged and a weak password is used it is possible for an attacker to break into the file and access your private keys.

## Create Wallet - Local

> It is critical that you understand the requirements of backing up and storing wallets generated via the CLI. Sharing or losing the mnemonic or file(s) used to store your keys can results in complete loss of funds.

Creating a wallet is simple, this example will create a wallet and add it to your computers memory.

```
switcheocli keys add <Key Name>
```

The output will look similar to the following:
```
{
    "name": "<Key Name>",
    "type": "local",
    "address": "swth1en….", # this is your Switcheo TradeHub adddress
    "pubkey": "swthpub1add...",
    "mnemonic": "empower double mansion ..." # save this!
}
```

## Create Wallet - File

It is also possible to have the keys added as a file to your filesystem location defined by your `switcheocli` directory.

```
switcheocli keys add <Key Name> \
  --keyring-backend file
```

## Recover Wallet

Regardless of how you have stored your wallet you can always recover your wallet information with the backed up mnemonic.

```
switcheocli keys add <Key Name> \
  --recover
```

This will then ask you to input your `bip39` mnemonic as well as the keyring password.

## List Keys in Wallet

To see what keys you currently have in your local keyring you can run the following command:

```
switcheocli keys list
```

Or if the keys are stored in a file.

```
switcheocli keys list --keyring-backend file
```

## Check Account Balance

```
switcheocli query account <TradeHub Address>
```

## Send Transaction

This example will send 10 SWTH to the address specified. Remember that values have to include all decimal places.

```
/switcheocli tx bank send \
  --from switcheolytics \
  --yes \
  --fees 100000000swth \
  -b block \
  --dry-run \
  <Key Name> <Receiver Address> <1000000000>swth
```

## Stake Transaction

To execute this function you will be required to find the validators address from the list of public validators on [TradeHub](https://switcheo.org)

**NOTE**: Before executing this command you need to understand that there will be a 30 day unbonding period before you can access these funds again.

```
switcheocli tx staking delegate \
  <Validator Address> \
  <SWTH Stake Amount> \
  --from <Key Name> \
  --fees 100000000swth \
  --yes \
  -b block \
  --chain-id switcheo-tradehub-1 \
  --dry-run
```

## Transfer Stake Transaction

When executing this command, it will transfer funds you have currently staked in one validator and transfer it to another.

> **NOTE**: This transaction is also constrained by the bonding period; Meaning you can transfer from A -> B but you have to wait 30 days to transfer from B -> C

```
switcheocli tx staking redelegate \
  <Current Validator Address> \
  <Transfer to Validator Address> \
  <SWTH Transfer Amount> \
  --fees 100000000swth \
  --gas auto \
  -b block \
  --from <Key Name> \
  --dry-run
```

## Withdraw Staking Rewards

This command will withdraw your staking rewards from the validator address specified in the command.

> This is not as efficient as staking again with a validator, which also triggers a withdraw in the same transaction.


```
switcheocli tx distribution withdraw-rewards \
  <Validator Address Claiming From> \
  --from <Key Name> \
  --fees 100000000swth \
  --dry-run
```

## Withdrwaw All Staking Rewards

This command will withdraw all current staking rewards from all the validator's you are staking to. You will need to take into consideration all the different validators and pay the appropriate fee. i.e.: 5 validators = 5 SWTH in fees

```
switcheocli tx distribution withdraw-all-rewards \
  --from <Key Name> \
  --fees <Fee Amount>swth \
  --gas auto \
  --dry-run
```

