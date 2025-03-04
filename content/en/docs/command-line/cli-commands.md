---
title: "CLI Commands"
key: "cli-commands"
description: ""
lead: ""
date: Thu Dec 29 2022 03:03:46 GMT-0800 (Pacific Standard Time)
lastmod: Thu Dec 29 2022 03:03:46 GMT-0800 (Pacific Standard Time)
draft: false
images: []
weight: 1
toc: true

menu:
    docs:
        parent: "command-line"

---
CLI Commands
============

The client used to interact with the Akash network is currently distributed in the `provider-services` Command Line Interface (CLI) application.

The Akash CLI
-------------

The Akash command line utility

     provider-services -h, --help   help for command line utility
    

Provider-Services Commands
--------------------------

Below are links to the top level commands. Click one of the links to see the available commands.

*   [provider-services](../cli/provider-services.md) -
*   [provider-services add-genesis-account](../cli/provider-services_add-genesis-account.md) - Add a genesis account to genesis.json
*   [provider-services auth-server](../cli/provider-services_auth-server.md) - Run the authentication server to issue JWTs to tenants
*   [provider-services collect-gentxs](../cli/provider-services_collect-gentxs.md) - Collect genesis txs and output a genesis.json file
*   [provider-services debug](../cli/provider-services_debug.md) - Tool for helping with debugging your application
*   [provider-services events](../cli/provider-services_events.md) - Prints out akash events in real time
*   [provider-services hostname-operator](../cli/provider-services_hostname-operator.md) - kubernetes operator interfacing with k8s nginx ingress
*   [provider-services init](../cli/provider-services_init.md) - Initialize private validator, p2p, genesis, and application configuration files
*   [provider-services ip-operator](../cli/provider-services_ip-operator.md) - kubernetes operator interfacing with Metal LB
*   [provider-services keys](../cli/provider-services_keys.md) - Manage your application's keys
*   [provider-services lease-events](../cli/provider-services_lease-events.md) - get lease events
*   [provider-services lease-logs](../cli/provider-services_lease-logs.md) - get lease logs
*   [provider-services lease-shell](../cli/provider-services_lease-shell.md) - do lease shell
*   [provider-services lease-status](../cli/provider-services_lease-status.md) - get lease status
*   [provider-services migrate](../cli/provider-services_migrate.md) -
*   [provider-services migrate-endpoints](../cli/provider-services_migrate-endpoints.md) - migrate endpoints between deployments on the same provider
*   [provider-services migrate-hostnames](../cli/provider-services_migrate-hostnames.md) - migrate hostnames between deployments on the same provider
*   [provider-services node](../cli/provider-services_node.md) - operations with akash RPC node
*   [provider-services operator](../cli/provider-services_operator.md) - kubernetes operators control
*   [provider-services query](../cli/provider-services_query.md) - Querying subcommands
*   [provider-services run](../cli/provider-services_run.md) - run akash provider
*   [provider-services run-resource-server](../cli/provider-services_run-resource-server.md) - Run the resource server which authenticates tenants based on JWT before providing access to resources
*   [provider-services send-manifest](../cli/provider-services_send-manifest.md) - Submit manifest to provider(s)
*   [provider-services service-status](../cli/provider-services_service-status.md) - get service status
*   [provider-services show-cluster-ns](../cli/provider-services_show-cluster-ns.md) - print cluster namespace for given lease ID
*   [provider-services status](../cli/provider-services_status.md) - get provider status
*   [provider-services tx](../cli/provider-services_tx.md) - Transactions subcommands
*   [provider-services validate-genesis](../cli/provider-services_validate-genesis.md) - validates the genesis file at the default location or at the location passed as an arg
*   [provider-services version](../cli/provider-services_version.md) - Print the application binary version information

Common Command Usage and Examples
---------------------------------

### Send Tokens

Sign and send tokens to other account.

#### **Usage**

    provider-services tx bank send [from_key_or_address] [to_address] [amount] [flags]
    

**Example**

    provider-services tx bank send bob akash12wlzqjelrt87r3u56ps4m8lk7wavx5m5jg9cax 10000000uakt --chain-id devnet -y
    
    {"height":"0","txhash":"116ED246AFF9F9B58036AECAA5EFE81AA7A788CC625CC2A4ADAFC68378834413","raw_log":"[]"}
    

**More info**

    provider-services tx send -h
    Send funds from one account to another. Note, the'--from' flag is
    ignored as it is implied from [from_key_or_address].
    
    Usage:
      provider-services tx bank send [from_key_or_address] [to_address] [amount] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for send
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Query Transaction

Query for a transaction by hash in a committed block.

**Usage**

    provider-services query tx <txhash> -o json
    

**Examples**

    provider-services query tx BCAB9AAC8C4F920218757A0C4461AF6C380A2144B4762B4DE1CE014BE2714DA5 -o json
    
    {"height":"36","txhash":"BCAB9AAC8C4F920218757A0C4461AF6C380A2144B4762B4DE1CE014BE2714DA5","codespace":"","code":0,"data":"0A060A0473656E64","raw_log":"[{\"events\":[{\"type\":\"message\",\"attributes\":[{\"key\":\"action\",\"value\":\"send\"},{\"key\":\"sender\",\"value\":\"akash16q6s0tauc3cks5us7f57wds8c8lqg4jqs0qtaf\"},{\"key\":\"module\",\"value\":\"bank\"}]},{\"type\":\"transfer\",\"attributes\":[{\"key\":\"recipient\",\"value\":\"akash1zsgzee6vvx942c4c69vl859w9azn77j8uhduug\"},{\"key\":\"sender\",\"value\":\"akash16q6s0tauc3cks5us7f57wds8c8lqg4jqs0qtaf\"},{\"key\":\"amount\",\"value\":\"100000stake\"}]}]}]","logs":[{"msg_index":0,"log":"","events":[{"type":"message","attributes":[{"key":"action","value":"send"},{"key":"sender","value":"akash16q6s0tauc3cks5us7f57wds8c8lqg4jqs0qtaf"},{"key":"module","value":"bank"}]},{"type":"transfer","attributes":[{"key":"recipient","value":"akash1zsgzee6vvx942c4c69vl859w9azn77j8uhduug"},{"key":"sender","value":"akash16q6s0tauc3cks5us7f57wds8c8lqg4jqs0qtaf"},{"key":"amount","value":"100000stake"}]}]}],"info":"","gas_wanted":"200000","gas_used":"57508","tx":{"@type":"/cosmos.tx.v1beta1.Tx","body":{"messages":[{"@type":"/cosmos.bank.v1beta1.MsgSend","from_address":"akash16q6s0tauc3cks5us7f57wds8c8lqg4jqs0qtaf","to_address":"akash1zsgzee6vvx942c4c69vl859w9azn77j8uhduug","amount":[{"denom":"stake","amount":"100000"}]}],"memo":"","timeout_height":"0","extension_options":[],"non_critical_extension_options":[]},"auth_info":{"signer_infos":[{"public_key":{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"A+hCkyWd4cWG0KD+GgCxHEOUzll1cl5VvoGgDvVIwF3E"},"mode_info":{"single":{"mode":"SIGN_MODE_DIRECT"}},"sequence":"1"}],"fee":{"amount":[],"gas_limit":"200000","payer":"","granter":""}},"signatures":["q3XqohxwkgaT0nLusXLaZ5aRGrcxbTUGS2pYN+tSPtkk10Ij+2YXs3LhXUxhcSNnTMABq4bIhJ3L/QDoz8Xp+w=="]},"timestamp":"2021-02-10T10:08:40Z"}
    

**More info**

    provider-services query tx -h
    
    Usage:
      provider-services query tx [hash] [flags]
    
    Flags:
          --height int      Use a specific height to query state at (this can error if the node is pruning state)
      -h, --help            help for tx
          --node string     <host>:<port> to Tendermint RPC interface for this chain (default "tcp://localhost:26657")
      -o, --output string   Output format (text|json) (default "text")
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Bond(Stake) Tokens

Delegate some tokens to validator i.e., bonding tokens.

**Usage**

    provider-services tx staking delegate <validator-address> <amount-with-denom> --from <from-account> -y
    

**Example**

    provider-services tx staking delegate akashvaloper1qgjla78dk2yk2eh6dmjeejz6m374ykdtpgp92s 1000000uakt --chain-id devnet --from alice -y
    
    {"height":"0","txhash":"F48C925F2F37766660D044DCAD0DC9A4CF51E454E184BC817EFD32ADA501ADD7","raw_log":"[]"}
    

**More info**

    provider-services tx staking delegate -h
    Delegate an amount of liquid coins to a validator from your wallet.
    
    Usage:
      provider-services tx staking delegate [validator-addr] [amount] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for delegate
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Redelegate Tokens

Redelegate some tokens from one validator to another.

**Usage**

    provider-services tx staking redelegate <src-validator-address> <dest-validator-address> <amount-with-denom> --from <from-account> -y -o json
    

**Example**

    provider-services tx staking redelegate akashvaloper1qgjla78dk2yk2eh6dmjeejz6m374ykdtpgp92s akashvaloper16q6s0tauc3cks5us7f57wds8c8lqg4jq6dwddr 1000000uakt --chain-id devnet --from alice -y -o json
    
    {"height":"0","txhash":"295A56A7B4DA7DE3266329981945307FF73ACFF1CCD319D1E1AE53DF16E0125E","raw_log":"[]"}
    

**More info**

    provider-services tx staking redelegate -h
    Redelegate an amount of illiquid staking tokens from one validator to another.
    
    Example:
    $ provider-services tx staking redelegate akashvaloper1gghjut3ccd8ay0zduzj64hwre2fxs9ldmqhffj akashvaloper1l2rsakp388kuv9k8qzq6lrm9taddae7fpx59wm 100stake --from mykey
    
    Usage:
      provider-services tx staking redelegate [src-validator-addr] [dst-validator-addr] [amount] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for redelegate
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Undelegate(unbond) Tokens

Undelegate some tokens from validator i.e., unbonding tokens.

**Usage**

    $ provider-services tx staking unbond <validator-address> <amount-with-denom> --from <from-account> -y -o json
    

**Example**

    provider-services tx staking unbond akashvaloper1qgjla78dk2yk2eh6dmjeejz6m374ykdtpgp92s 1000000uakt --chain-id devnet --from alice -y -o json
    
    {"height":"0","txhash":"F48C925F2F37766660D044DCAD0DC9A4CF51E454E184BC817EFD32ADA501ADD7","raw_log":"[]"}
    

**More info**

    provider-services tx staking unbond -h
    Unbond an amount of bonded shares from a validator.
    
    Example:
    $ provider-services tx staking unbond akashvaloper1gghjut3ccd8ay0zduzj64hwre2fxs9ldmqhffj 100uakt --from mykey
    
    Usage:
      provider-services tx staking unbond [validator-addr] [amount] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for unbond
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Withdraw Rewards

Withdraw rewards from validator

**Usage**

    provider-services tx distribution withdraw-rewards <validator-address> <amount-with-denom> --from <from-account> -y -o json
    

**Example**

    provider-services tx distribution withdraw-rewards akashvaloper16q6s0tauc3cks5us7f57wds8c8lqg4jq6dwddr --chain-id devnet --from alice -y
    
    {"height":"0","txhash":"1BBB4A7A4D245C7534F366BABCE5BDD73776FB0430B3A241BFEEEF99445C52C3","raw_log":"[]"}
    

**More info**

    provider-services tx distribution withdraw-rewards -h
    Withdraw rewards from a given delegation address,
    and optionally withdraw validator commission if the delegation address given is a validator operator.
    
    Example:
    $ provider-services tx distribution withdraw-rewards akashvaloper1gghjut3ccd8ay0zduzj64hwre2fxs9ldmqhffj --from mykey
    
    ### Withdraw commission
    $ provider-services tx distribution withdraw-rewards akashvaloper1gghjut3ccd8ay0zduzj64hwre2fxs9ldmqhffj --from mykey --commission
    
    Usage:
      provider-services tx distribution withdraw-rewards [validator-addr] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --commission               Withdraw the validator's commission in addition to the rewards
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for withdraw-rewards
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Query Rewards

Query all rewards earned by a delegator, optionally restrict to rewards from a single validator.

**Usage**

    provider-services query distribution rewards <delegator-address> [<validator-address>] -o json
    

**Examples**

    provider-services query distribution rewards akash1gghjut3ccd8ay0zduzj64hwre2fxs9ld75ru9p akashvaloper16q6s0tauc3cks5us7f57wds8c8lqg4jq6dwddr -o json
    
    [{"denom":"uakt","amount":"69009.444000000000000000"}]
    
    $ provider-services query distribution rewards akash1gghjut3ccd8ay0zduzj64hwre2fxs9ld75ru9p -o json
    
    {"rewards":[{"validator_address":"akashvaloper16q6s0tauc3cks5us7f57wds8c8lqg4jq6dwddr","reward":[{"denom":"uakt","amount":"1467715.032000000000000000"}]}],"total":[{"denom":"uakt","amount":"1467715.032000000000000000"}]
    

**More info**

    provider-services query distribution rewards -h
    
    Usage:
      provider-services query distribution rewards [delegator-addr] [<validator-addr>] [flags]
    
    Flags:
          --height int      Use a specific height to query state at (this can error if the node is pruning state)
      -h, --help            help for rewards
          --node string     <host>:<port> to Tendermint RPC interface for this chain (default "tcp://localhost:26657")
      -o, --output string   Output format (text|json) (default "text")
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Query Balance

Query the total balance of an account or of a specific denomination.

**Usage**

    provider-services query bank balances <account-address>
    provider-services query bank balances <account-address> --denom=[denom]
    

**Examples**

    provider-services query bank balances akash16q6s0tauc3cks5us7f57wds8c8lqg4jqs0qtaf -o json
    
    {"balances":[{"denom":"stake","amount":"99899900000"},{"denom":"uakt","amount":"100000000000"}],"pagination":{"next_key":null,"total":"0"}}
    

**More info**

    provider-services query bank balances -h
    
    Usage:
      provider-services query bank balances [address] [flags]
    
    Flags:
          --count-total       count total number of records in all balances to query for
          --denom string      The specific balance denomination to query for
          --height int        Use a specific height to query state at (this can error if the node is pruning state)
      -h, --help              help for balances
          --limit uint        pagination limit of all balances to query for (default 100)
          --node string       <host>:<port> to Tendermint RPC interface for this chain (default "tcp://localhost:26657")
          --offset uint       pagination offset of all balances to query for
      -o, --output string     Output format (text|json) (default "text")
          --page uint         pagination page of all balances to query for. This sets offset to a multiple of limit (default 1)
          --page-key string   pagination page-key of all balances to query for
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Recover Key

Provide seed phrase to recover existing key instead of creating.

**Usage**

    provider-services keys add <key-name> --recover
    

**Example**

    provider-services keys add alice --recover
    > Enter your bip39 mnemonic
    close super rare vicious core supreme collect fatigue maid cupboard throw surge notable phrase brand actual high track stay visual afraid lot dizzy wedding
    
    - name: alice
      type: local
      address: akash12wlzqjelrt87r3u56ps4m8lk7wavx5m5jg9cax
      pubkey: akashpub1addwnpepqd80atzkr5c5teq933q80jkh27ljgwsm3r00fxjcl5nvaxkm9z0hqhw5h7e
      mnemonic: ""
      threshold: 0
      pubkeys: []
    

### Export Key

Export a private key from the local keybase in ASCII-armored encrypted format. Export key with entering new password.

**Usage**

    provider-services keys export <key-name>
    

**Example**

    provider-services keys export provider
    Enter passphrase to encrypt the exported key:
    -----BEGIN TENDERMINT PRIVATE KEY-----
    kdf: bcrypt
    salt: FC01B9FACA831E315C867E07A586AEF7
    type: secp256k1
    
    VmSk+mQl2tpra7dHt2Dm2z4S2unH2kbjXaOZTK/9NGQsw3TSb6GkwBU7WizTCmN/
    3dxPu/wdDa1uBLYg+zgYhTtK6HlPDrulxlDDQjg=
    =KGDA
    -----END TENDERMINT PRIVATE KEY-----
    

### Import Key

Import a file with ASCII armored private key into the local keybase. Required key password to import key.

**Usage**

    provider-services keys import <key-name> <keyfile>
    

**Example**

    provider-services keys import provider key
    Enter passphrase to decrypt your key:
    

### Generating a Transaction

Generating a transaction can simply be done by appending the --generate-only flag on any tx command

**Example**

    provider-services tx send bob akash12wlzqjelrt87r3u56ps4m8lk7wavx5m5jg9cax 10000000uakt --chain-id devnet --generate-only
    

This will output the unsigned transaction as JSON in the console. We can also save the unsigned transaction to a file by appending `> unsigned_tx.json` to the above command.

### Signing a Transaction

Signing a transaction using the CLI requires the unsigned transaction to be saved in a file.

    provider-services tx sign unsigned_tx.json --chain-id devnet --from alice
    

This command will decode the unsigned transaction and sign it with SIGN\_MODE\_DIRECT with alice's key, which we already set up in the keyring. The signed transaction will be output as JSON to the console, and we can save it to a file by appending `> signed_tx.json`.

**More Info**

    Usage:
      provider-services tx sign [file] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
          --amino                    Generate Amino encoded JSON suitable for submiting to the txs REST endpoint
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for sign
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --multisig string          Address of the multisig account on behalf of which the transaction shall be signed
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
          --output-document string   The document will be written to the given file instead of STDOUT
          --overwrite                Overwrite existing signatures with a new one. If disabled, new signature will be appended
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --signature-only           Print only the signatures
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    

Some useful flags to consider in the tx sign command:

*   \--sign-mode: you may use amino-json to sign the transaction using SIGN\_MODE\_LEGACY\_AMINO\_JSON
*   \--offline: sign in offline mode. This means that the tx sign command doesn't connect to the node to retrieve the signer's account number and sequence, both needed for signing. In this case, you must manually supply the --account-number and --sequence flags. This is useful for offline signing, i.e. signing in a secure environment which doesn't have access to the internet.

### Encode a Transaction

Encode transactions created with the --generate-only flag and signed with the sign command. It will read a transaction from , serialize it to the Amino wire protocol, and output it as base64. If you supply a dash (-) argument in place of an input filename, the command reads from standard input.

    provider-services tx encode signed-tx.json
    
    CpABCo0BChwvY29zbW9zLmJhbmsudjFiZXRhMS5Nc2dTZW5kEm0KLGFrYXNoMTZxNnMwdGF1YzNja3M1dXM3ZjU3d2RzOGM4bHFnNGpxczBxdGFmEixha2FzaDF6c2d6ZWU2dnZ4OTQyYzRjNjl2bDg1OXc5YXpuNzdqOHVoZHV1ZxoPCgVzdGFrZRIGMTAwMDAwElgKUApGCh8vY29zbW9zLmNyeXB0by5zZWNwMjU2azEuUHViS2V5EiMKIQPoQpMlneHFhtCg/hoAsRxDlM5ZdXJeVb6BoA71SMBdxBIECgIIfxgCEgQQwJoMGkB+VlYeHU81v4qxIOGpIKpmq7fzVB83Lvy5xvxpm37F6yZ9+XA56KzkMdHhpURmaFYF2567D0nE5e57UKfKF6Az
    

**More Info**

    Usage:
      provider-services tx encode [file] [flags]
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for encode
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

### Broadcasting a Transaction (CLI)

Broadcasting a transaction using the CLI requires the signed transaction to be saved in a file.

    provider-services tx broadcast [file_path] [flags]
    

You may optionally pass the --broadcast-mode flag to specify which response to receive from the node:

*   block: the CLI waits for the tx to be committed in a block.
*   sync: the CLI waits for a CheckTx execution response only.
*   async: the CLI returns immediately (transaction might fail).

**More info**

    Example:
    
    $ provider-services tx broadcast ./mysign.json
    
    Flags:
      -a, --account-number uint      The account number of the signing account (offline mode only)
      -b, --broadcast-mode string    Transaction broadcasting mode (sync|async|block) (default "sync")
          --dry-run                  ignore the --gas flag and perform a simulation of a transaction, but don't broadcast it
          --fees string              Fees to pay along with transaction; eg: 10uatom
          --from string              Name or address of private key with which to sign
          --gas string               gas limit to set per-transaction; set to "auto" to calculate sufficient gas automatically (default 200000)
          --gas-adjustment float     adjustment factor to be multiplied against the estimate returned by the tx simulation; if the gas limit is set manually this flag is ignored  (default 1)
          --gas-prices string        Gas prices in decimal format to determine the transaction fee (e.g. 0.1uatom)
          --generate-only            Build an unsigned transaction and write it to STDOUT (when enabled, the local Keybase is not accessible)
      -h, --help                     help for broadcast
          --keyring-backend string   Select keyring's backend (os|file|kwallet|pass|test) (default "os")
          --keyring-dir string       The client Keyring directory; if omitted, the default 'home' directory will be used
          --ledger                   Use a connected Ledger device
          --memo string              Memo to send along with transaction
          --node string              <host>:<port> to tendermint rpc interface for this chain (default "tcp://localhost:26657")
          --offline                  Offline mode (does not allow any online functionality
      -s, --sequence uint            The sequence number of the signing account (offline mode only)
          --sign-mode string         Choose sign mode (direct|amino-json), this is an advanced feature
          --timeout-height uint      Set a block timeout height to prevent the tx from being committed past a certain height
      -y, --yes                      Skip tx broadcasting prompt confirmation
    
    Global Flags:
          --chain-id string     The network chain ID
          --home string         directory for config and data (default "/home/vitwit/.akash")
          --log_format string   The logging format (json|plain) (default "plain")
          --log_level string    The logging level (trace|debug|info|warn|error|fatal|panic) (default "info")
          --trace               print out full stack trace on errors
    

Broadcasting a Transaction (REST)
---------------------------------

Broadcasting a transaction using the REST endpoint (served by gRPC-gateway) can be done by sending a POST request as follows, where the txBytes are the protobuf-encoded bytes of a signed transaction:

    curl -X POST -H "Content-Type: application/json" -d'{"tx_bytes":"{{txBytes}}","mode":"BROADCAST_MODE_SYNC"}' localhost:1317/cosmos/tx/v1beta1/txs
    

Here, `tx_bytes` value will be encoded tx of signed transaction.

**Example**

    $ $ curl -X POST -H "Content-Type: application/json" -d'{"tx_bytes":"CpABCo0BChwvY29zbW9zLmJhbmsudjFiZXRhMS5Nc2dTZW5kEm0KLGFrYXNoMTZxNnMwdGF1YzNja3M1dXM3ZjU3d2RzOGM4bHFnNGpxczBxdGFmEixha2FzaDF6c2d6ZWU2dnZ4OTQyYzRjNjl2bDg1OXc5YXpuNzdqOHVoZHV1ZxoPCgVzdGFrZRIGMTAwMDAwElgKUApGCh8vY29zbW9zLmNyeXB0by5zZWNwMjU2azEuUHViS2V5EiMKIQPoQpMlneHFhtCg/hoAsRxDlM5ZdXJeVb6BoA71SMBdxBIECgIIfxgCEgQQwJoMGkB+VlYeHU81v4qxIOGpIKpmq7fzVB83Lvy5xvxpm37F6yZ9+XA56KzkMdHhpURmaFYF2567D0nE5e57UKfKF6Az","mode":"BROADCAST_MODE_SYNC"}' localhost:1317/cosmos/tx/v1beta1/txs
    

Using CosmJS (JavaScript & TypeScript)
--------------------------------------

CosmJS aims to build client libraries in JavaScript that can be embedded in web applications. Please see [CosmJS documentation](https://cosmos.github.io/cosmjs/) for more information. As of January 2021, CosmJS documentation is still work in progress.

Please go through this [code](https://github.com/chainapsis/keplr-example/blob/5c95ce0c4878f40ccf40931bc54a170af4a46fa2/src/main.js) to sign a transaction using CosmJS javascript library.