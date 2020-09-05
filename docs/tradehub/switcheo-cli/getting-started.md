`switcheocli`

The switcheocli is a tool that allows users to interact with Switcheo TradeHub from a command prompt without requiring the UI of switcheo.org

This allows users to automate tasks or perform lookups against on-chain data.

There are 2 methods that `switcheocli` gets installed:

1. Direct Download
2. Installed as part of the Validator setup

Previous sections have covered each of the options listed above, once the CLI has been installed there are a couple of steps required to get started and this guide is designed to briefly touch on common steps a new user would face using a fresh CLI client.

## Create or Import Wallet

Building from a freshly installed `switcheocli` there are a couple of items to define before moving forward:

1. Wallet Names
2. Secure storage of the mnemonic(s) that are generated
3. Location of the keyring methods to securely store it
4. Choosing a secure password

Each of these items will be critical for `ALL` commands with the CLI and will need to be consistent with how they are initially defined.

`<Key Name>` - This can be named anything so keep track of the naming convention used.
`<--keyring-backed file>` - Always include if you create your wallet with it, additionally, ensure this file is never shared since it is your wallet

### Create Wallet

It is also possible to have the keys added as a file to your filesystem location defined by your `switcheocli` directory.

```
switcheocli keys add <Key Name> <--keyring-backend file>
```

Select a strong password and note the mnemonic, store both in a secure location.

### Import Wallet

Regardless of how you have stored your wallet you can always recover your wallet information with the backed up mnemonic.

```
switcheocli keys add <Key Name> --recover <--keyring-backend file>
```

Enter the mnemonic and select a strong password, store this in a secure location.

## Fund wallet with Switcheo (SWTH)

The Switcheo token pays for transactions on TradeHub, it is required to have `at least 1 SWTH token` to pay for this fee. Please keep this in mind when transfering or staking, otherwise you may find that your can no longer submit transactions until you have topped the wallet off again. To get SWTH token on your wallet you will need to navigate to the deposit page on switcheo.org:

1. NEO -> TradeHub swap - https://switcheo.org/deposit

## Transfer funds

This example will send 10 SWTH to the address specified. Remember that values have to include all decimal places.

```
switcheocli tx bank send \
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