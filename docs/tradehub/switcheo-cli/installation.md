[Simple Switcheo CLI Staking Guide](https://blog.switcheo.network/switcheo-tradehub-cli-staking-guide/)

> Check the [Switcheo TradeHub GitHub](https://github.com/Switcheo/tradehub) page for most up to date information.

## Mac
```
curl -L https://github.com/Switcheo/tradehub/releases/download/v1.5.0/switcheocli-osx-x64.tar.gz | tar -xz
```

## Linux
```
curl -L https://github.com/Switcheo/tradehub/releases/download/v1.5.0/switcheocli-linux-x64.tar.gz | tar -xz
```

## Configuration

> By default the configuration will be configured in the users home directory ~/.switcheocli/config

Pick Validator Node to connect to, by default this is configured for one of Switcheo's nodes.

```
switcheocli config node <tcp://ip:26657>
```

TODO: Add list of verified validators

Set the default value of trust for the node we just configured. If this is your own node you can set this to true but out of caution it is best to set this to false.
```
switcheocli config trust-node false
```

Setup the Chain ID

* Mainnet - switcheo-tradehub-1
* Testnet - switcheochain

```
switcheocli config chain-id switcheo-tradehub-1
```
