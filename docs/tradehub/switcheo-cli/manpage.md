This page is meant to cover the different functions that the switcheocli utility has available for end users. This is an attempt to make this process smother and document the different options and variation.

## Configuration

When using the switcheocli you can save time and keystrokes by setting a couple of default variables. The <Node> and the <Chain ID>.

```
switcheocli config node tcp://<IP or hostname>:26657
switcheocli config chain-id <switcheo-tradehub-1>
```

The configuration above will be stored in the default location for the user at:

> ~/.switcheocli/config/config.toml 

```
chain-id = "<switcheo-tradehub-1>"
node = "tcp://<IP or hostname>:26657"
```

NOTE: These values can be overriden by passing the appropriate flag for each command.

## Available Commands

```
Switcheo TradeHub Client

Usage:
  switcheocli [command]

Available Commands:
  status      Query remote node for status
  config      Create or query an application CLI configuration file
  query       Querying subcommands
  tx          Transactions subcommands
  db          Database subcommands
              
  rest-server Start LCD (light-client daemon), a local REST server
              
  keys        Add or view local private keys
              
  help        Help about any command

Flags:
      --chain-id string   Chain ID of tendermint node
  -e, --encoding string   Binary encoding (hex|b64|btc) (default "hex")
  -h, --help              help for switcheocli
      --home string       directory for config and data (default "/root/.switcheocli")
  -o, --output string     Output format (text|json) (default "text")
      --trace             print out full stack trace on errors

Use "switcheocli [command] --help" for more information about a command.
```

## Status

The status command can be used to check in on the status of a specific node. By default this command will use the configurations setup during the configuration setup or you can define each specific configs via the Global Flags listed below.

```
Query remote node for status

Usage:
  switcheocli status [flags]

Flags:
  -h, --help          help for status
      --indent        Add indent to JSON response
  -n, --node string   Node to connect to (default "tcp://localhost:26657")

Global Flags:
      --chain-id string   Chain ID of tendermint node
  -e, --encoding string   Binary encoding (hex|b64|btc) (default "hex")
      --home string       directory for config and data (default "/root/.switcheocli")
  -o, --output string     Output format (text|json) (default "text")
      --trace             print out full stack trace on errors
```


## Querying

This subcommand allows users to query a blockchain node for specific information. There are many options available here but the most common will be querying an account balance and an example of that is shown below.

```
Querying subcommands

Usage:
  switcheocli query [command]

Aliases:
  query, q

Available Commands:
  account                  Query account balance
              
  tendermint-validator-set Get the full tendermint validator set at given height
  block                    Get verified data for a the block at given height
  txs                      Query for paginated transactions that match a set of events
  tx                       Query for a transaction by hash in a committed block
              
  distribution             Querying commands for the distribution module
  pricing                  Querying commands for the pricing module
  subaccount               Querying commands for the subaccount module
  btcx                     Querying commands for the btcx module
  ft                       Querying commands for the ft module
  auth                     Querying commands for the auth module
  mint                     Querying commands for the minting module
  autodeleverage           Querying commands for the autodeleverage module
  liquidation              Querying commands for the liquidation module
  staking                  Querying commands for the staking module
  headersync               Querying commands for the headersync module
  lockproxypip1            Querying commands for the lockproxypip1 module
  slashing                 Querying commands for the slashing module
  oracle                   Querying commands for the oracle module
  coin                     Querying commands for the token module
  coin                     Querying commands for the token module
  ccm                      Querying commands for the ccm module
  supply                   Querying commands for the supply module

Flags:
  -h, --help   help for query

Global Flags:
      --chain-id string   Chain ID of tendermint node
  -e, --encoding string   Binary encoding (hex|b64|btc) (default "hex")
      --home string       directory for config and data (default "/root/.switcheocli")
  -o, --output string     Output format (text|json) (default "text")
      --trace             print out full stack trace on errors

Use "switcheocli query [command] --help" for more information about a command.
```

Find a specifc addresses account balance.

```
switcheocli query account swth<address>
```

## Transactions

This section of the `switcheocli` utility is heavily used and has the following options available to it.

```
Transactions subcommands

Usage:
  switcheocli tx [command]

Available Commands:
  send           Create and sign a send tx
              
  sign           Sign transactions generated offline
  multisign      Generate multisig signatures for transactions generated offline
              
  broadcast      Broadcast transactions generated offline
  encode         Encode transactions generated offline
              
  staking        Staking transaction subcommands
  distribution   Distribution transactions subcommands
  lockproxypip1  lockproxypip1 module send transaction subcommands
  pricing        pricing transactions subcommands
  autodeleverage autodeleverage transactions subcommands
  coin           Token transaction subcommands
  ccm            ccm module send transaction subcommands
  liquidation    liquidation transactions subcommands
  oracle         Oracle transaction subcommands
  coin           Token transaction subcommands
  btcx           btcx module send transaction subcommands
  headersync     headersync module send transaction subcommands
  slashing       Slashing transactions subcommands
  auth           Auth transaction subcommands
  subaccount     Subaccount transaction subcommands
  ft             ft module send transaction subcommands
  bank           Bank transaction subcommands

Flags:
  -h, --help   help for tx

Global Flags:
      --chain-id string   Chain ID of tendermint node
  -e, --encoding string   Binary encoding (hex|b64|btc) (default "hex")
      --home string       directory for config and data (default "/root/.switcheocli")
  -o, --output string     Output format (text|json) (default "text")
      --trace             print out full stack trace on errors

Use "switcheocli tx [command] --help" for more information about a command.
```


## Keys

```
Keys allows you to manage your local keystore for tendermint.

    These keys may be in any format supported by go-crypto and can be
    used by light-clients, full nodes, or any other application that
    needs to sign with a private key.

Usage:
  switcheocli keys [command]

Available Commands:
  mnemonic    Compute the bip39 mnemonic for some input entropy
  add         Add an encrypted private key (either newly generated or recovered), encrypt it, and save to disk
  export      Export private keys
  import      Import private keys into the local keybase
  list        List all keys
  show        Show key info for the given name
              
  delete      Delete the given keys
  parse       Parse address from hex to bech32 and vice versa
  migrate     Migrate keys from the legacy (db-based) Keybase

Flags:
  -h, --help                     help for keys
      --keyring-backend string   Select keyring's backend (os|file|test) (default "os")

Global Flags:
      --chain-id string   Chain ID of tendermint node
  -e, --encoding string   Binary encoding (hex|b64|btc) (default "hex")
      --home string       directory for config and data (default "/root/.switcheocli")
  -o, --output string     Output format (text|json) (default "text")
      --trace             print out full stack trace on errors

Use "switcheocli keys [command] --help" for more information about a command.
```
