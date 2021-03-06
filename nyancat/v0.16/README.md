# Nyancat Testnet V0.16

To support `DeFi` functionalities, we introduced the [HTLC](https://www.irisnet.org/docs/features/htlc.html) and [Coin Swap](https://www.irisnet.org/docs/features/coinswap.html) modules in v0.16, so that users can swap tokens between different blockchains and trade them in a decentralized manner.

## Latest version: [v0.16.0](https://github.com/irisnet/irishub/releases/tag/v0.16.0)

**Note**:

- The point-to-`iris` conversion rate will be announced at the end of this incentivized testnet campaign.

- For every task, only the top 40 completed validators can get rewards (the upgrade task is based on the voting order of the upgrade proposal, if a valid voter doesn't complete the upgrade in time, the reward will be extended to the next completed validator)

## v0.16.0

### HTLC Tasks

[HTLC](https://www.irisnet.org/docs/features/htlc.html) is mostly used in cross-chain atomic swaps. This task is gonna be very interesting:

| NO. | Name                | Details                                 | Points |
| --- | ------------------- | --------------------------------------- | ------ |
| 7   | Claim testnet rewards | Claim testnet rewards on Mainnet via HTLC | 30     |

**Note:**

- Please use your testnet validator's operator account (which account you used to create the testnet validator) to sign the testnet transactions, so that we can verify the task completion.
- This task is optional for claiming the rewards, you can decide not to do this task, then we can send you the OTHER TASK REWARDS(except HTLC) directly([your signature is required](./reward-claims/README.md#submit-signature))

This is a special task, it can only be done **AFTER** the Mainnet upgrade. You will need to do as the following steps:

- [Submit your signature](./reward-claims/README.md#submit-signature)
- Contact @Yelong in the community, make sure he is online (His time zone is UTC+8)
- You [Create an HTLC](https://www.irisnet.org/docs/cli-client/htlc.html#iriscli-htlc-create) on `nyancat-6`, specifying: `--to="faa1svannhv2zaxefq83m7treg078udfk37lvvs7t5"`
- Send @Yelong your HTLC tx hash, wait for him to create another HTLC on `irishub` with your hash-lock
- Confirm your rewards and [Claim](https://www.irisnet.org/docs/cli-client/htlc.html#iriscli-htlc-claim) on `irishub`
- [Check status](https://www.irisnet.org/docs/cli-client/htlc.html#iriscli-htlc-query-htlc)

## ~~v0.16.0-rc1~~ Done

### ~~Upgrade Tasks~~ Done

#### Steps

1. Join `nyancat-6` and set up your validator before the `Upgrade Proposal`.

2. Upgrade Proposal: `2019-11-19 13:00:00 (UTC)`, we'll have 24 hours to vote. If you are not a validator in `nyancat-6`, please create one before the upgrade proposal, so as not to affect the acquisition of upgrade task points.

3. Version Switching: `2019-11-21 05:00:00 (UTC)`, which means we'll have 16 hours to upgrade our nodes to the new version after the upgrade proposal passed.

You can refer to the [Mainnet Upgrade Preview](https://github.com/irisnet/mainnet/blob/master/upgrade/v0.16.0.md) for detailed upgrade process.

**Note:**

- Only the top 40 completed validators can get rewards
- The `top 40` is based on the voting order of the upgrade proposal, if a valid voter doesn't complete the upgrade in time, the reward will be extended to the next completed validator
- The upgraded validators are required to have at least one valid `Precommit` in the `first 300 blocks` since the version switching, which means you need to upgrade your validator before the version switching, and make sure it is running after the version switching.

| No  | Name                   | Details                                               | Points |
| --- | ---------------------- | ----------------------------------------------------- | ------ |
| 6   | Upgrade to v0.16.0-rc1 | Rehearse the mainnet upgrade from v0.15.\* to v0.16.0 | 60     |

## ~~v0.16.0-rc0~~ Done

Just as we did on the testnets for v0.15, we'll first test drive the new features of v0.16 on a new testnet `nyancat-5`, if everything works fine, we then go through the on-chain upgrade process on `nyancat-6`.

### ~~Coin Swap Tasks~~ Done

Coinswap relies on dynamic data to calculate exchange rates in real time, making it difficult to initiate transactions using the command line. So the coinswap module only has the [Restful API](https://lcd.nyancat.irisnet.org/swagger-ui/#/CoinSwap). We have a demo web tool to help you understand and complete the tasks: [Coinswap Demo](https://coinswap.nyancat.irisnet.org/).

If you have a Ledger hardware, it will be easy to do the tasks with the web tool. Otherwise you can only use the [Restful API](https://lcd.nyancat.irisnet.org/swagger-ui/#/CoinSwap) to generate unsigned transactions and [sign them offline](https://www.irisnet.org/docs/cli-client/tx.html#iriscli-tx-sign), then [broadcast](https://www.irisnet.org/docs/cli-client/tx.html#iriscli-tx-broadcast).

Read more about [IRISHub Coin Swap](https://www.irisnet.org/docs/features/coinswap.html)

**Note:** Please use your testnet validator's operator account (which account you used to create the validator) to sign the transactions, so that we can verify the task completion.

| NO. | Name             | Details                                  | Points |
| --- | ---------------- | ---------------------------------------- | ------ |
| 1   | Add Liquidity    | Deposit liquidity to the reserve pool    | 20     |
| 2   | Remove Liquidity | Withdraw liquidity from the reserve pool | 20     |
| 3   | IRIS-Token Swap  | Buy or sell some BTC with/for IRIS       | 20     |
| 4   | Token-Token Swap | Buy or sell some ETH with/for BTC        | 20     |

### ~~Snapshot Tasks~~ Done

Since the block data gets bigger and bigger, making it more and more difficult to backup or to sync from scratch.

From v0.16, some of the IRISHub nodes (such as validators, sentries, seeds) will no longer need to retain all historical data.

- You can choose to drop the data of a node which before a certain block height to free up disk space.
- You can quickly start up a new node without syncing all historical data.

Read more about [IRISHub Snapshot](https://www.irisnet.org/docs/daemon/snapshot.html)

**Note:** Please comment your PGP-ID: RPC-Address (:26657) [HERE](https://github.com/irisnet/testnets/issues/406), so we can verify the task completion.

| NO. | Name                 | Details                                            | Points |
| --- | -------------------- | -------------------------------------------------- | ------ |
| 5   | Prune your node data | Drop the historical data and start with a snapshot | 30     |
