# etchash
`etchash` is the modified dagger hashimoto used by ethereum classic. it is comparable in it's behaviour to ethereum foundation's [ethash](https://en.wikipedia.org/wiki/Ethash) but allows for a long-term viability of gpu-mining with cards that have low memory (3gb, 4gb, 6gb) available.

this repository contains an overview of the specification, and tries to point to existing implementations of clients, pools, miners, and other tooling relevant for `etchash`.

### specification

`etchash` was first brought up and specified by luke williams (**[@iquidus](https://github.com/iquidus)**) in september 2020. the full specifcation can be found in [ecip-1099: calibrate epoch duration](https://github.com/ethereumclassic/ECIPs/blob/master/_specs/ecip-1099.md). the idea is to calibrate the epoch length used in dag calculations, effectively doubling epoch durations and therefore reducing the dag size significantly and slowing down dag growth drastically.

it was used to replace the old specification [ecip-1043: fixed dag limit restriction](https://github.com/ethereumclassic/ECIPs/blob/master/_specs/ecip-1043.md) published by cody burns (**[@realcodywburns](https://github.com/realcodywburns)**) and wolf spraul (**[@wolf-linzhi](https://github.com/wolf-linzhi)**) in april 2018.

additional `etchash` test cases can be found here: [ecip-1099-data](https://github.com/iquidus/ecip-1099-data).

### networks powered by etchash

[ethereum classic](https://ethereumclassic.org) transitions from `ethash` to `etchash` on block `11_700_000` (eth/64 forkid `0xdb63a1ca`) which marks the epoch boundary `390 --> 195` according to the specification. the estimated activation date is expected to happen around december 2nd, 2020.
* classic status dashboard: https://classic.dash.fault.dev/
* classic fork monitoring: https://classic.fork.fault.dev/
* classic block explorer: https://blockscout.com/etc/mainnet/
* classic light explorer: https://expedition.dev/?network=mainnet

the [mordor classic testnet](https://github.com/eth-classic/mordor) already transitioned from `ethash` to `etchash` on block `2_520_000` (eth/64 forkid `0x66b5c286`) which marked the epoch boundary `82 --> 41` on october 18th, 2020.
* mordor status dashboard: https://mordor.dash.fault.dev/
* mordor fork monitoring: https://mordor.fork.fault.dev/
* mordor block explorer: https://blockscout.com/etc/mordor/
* mordor light explorer: https://expedition.dev/?network=mordor

the hard-fork activating `etchash` on the ethereum classic networks is code-named **thanos** upgrade, **etchash** fork, or **ecip-1099** transition.

### clients implementing etchash

core geth [`v1.11.16`](https://github.com/etclabscore/core-geth/releases/tag/v1.11.16) or later
* github https://github.com/etclabscore/core-geth
* pull-requests [#186](https://github.com/etclabscore/core-geth/pull/186) [#209](https://github.com/etclabscore/core-geth/pull/209) [#212](https://github.com/etclabscore/core-geth/pull/212)
* config name `ECIP1099FBlock`

hyperledger besu [`20.10.0-RC2`](https://github.com/hyperledger/besu/releases/tag/20.10.0-RC2) or later
* github https://github.com/hyperledger/besu
* pull-requests [#1421](https://github.com/hyperledger/besu/pull/1421) [#1462](https://github.com/hyperledger/besu/pull/1462)
* config name `thanosBlock`

### mining software support

open source:
* _:hourglass_flowing_sand: ethminer/etcminer (:clock11: unpublished)_

proprietary:
* nanominer [v1.12.0](https://github.com/nanopool/nanominer/releases/tag/v1.12.0)
* lolMiner [1.12](https://github.com/Lolliedieb/lolMiner-releases/releases/tag/1.12)
* GMiner [2.30](https://github.com/develsoftware/GMinerRelease/releases/tag/2.30)
* T-Rex [0.18.8](https://github.com/trexminer/T-Rex/releases/tag/0.18.8)
* NBMiner [v33.4](https://github.com/NebuTech/NBMiner/releases/tag/v33.4)
* _:hourglass_flowing_sand: PhoenixMiner 5.2 (:clock11: release pending)_

### mining pool software support

* https://github.com/etclabscore/open-etc-pool/
