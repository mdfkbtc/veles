Veles Core version 0.17.1.2 is now available from:

 <https://github.com/velescore/veles/releases/tag/v0.17.1.2/>

This is a new minor version release, porting **important masternode consensus
upgrade** to the 0.17 version from the current master branch 0.18. 
If you still wish to use 0.17 version instead of the latest 0.18, it **is highly 
recommended to update to version v0.17.1.2 before the block 240 000**, when new 
masternode collateral change will be enforced on the network.

Please report bugs using the issue tracker at GitHub:

  <https://github.com/velescore/veles/issues>

How to Upgrade
==============

If you are running an older version, shut it down. Wait until it has completely
shut down (which might take a few minutes for older versions), then run the
installer (on Windows) or just copy over `/Applications/Veles-Qt` (on Mac)
or `Velesd`/`Veles-qt` (on Linux).

Downgrading warning
-------------------

Wallets created in 0.16 and later are not compatible with versions prior to 0.16
and will not work if you try to use newly created wallets in older versions. Existing
wallets that were created with older versions are not affected by this. This might
be useful only for exporting of old private keys, as wallets of version v0.17.0.20
and older are not compatible with the current chain anymore.

Compatibility
==============

Veles Core is extensively tested on multiple operating systems using
the Linux kernel, macOS 10.8+, and Windows Vista and later. Windows XP is not supported.

Veles Core should also work on most other Unix-like systems but is not
frequently tested on them.

0.17.1.2 change log
------------------

### Masternodes
- #38 - mn: Backport collateral change to 500 VLS, force at block 240k


Thanks to everyone who directly contributed to this release:

- UhlikSK
- AltcoinBaggins

As well as everyone that helped to improve Veles Core with their suggestions at [Veles Discord](https://discord.gg/rXgH6Qn).
