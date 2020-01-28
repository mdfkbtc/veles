Veles Core version 0.18.x "Blockchain Barracuda" is now available from:

Download: <https://www.veles.network/download.en.html>

This is a new major version release, including new features, various bug
fixes and performance improvements, as well as updated translations.

Please report bugs using the issue tracker at GitHub:

  <https://github.com/velescore/veles/issues>
Veles Core version 0.18.1.3 is now available from:

 <https://github.com/velescore/veles/releases/tag/v0.18.1.3/>

This is a new minor version release, including performance and other
improvements.

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
be useful only for exporting of old private keys, as wallets of version v0.18.0.20
and older are not compatible with the current chain anymore.

Compatibility
==============

Veles Core is extensively tested on multiple operating systems using
the Linux kernel, macOS 10.8+, and Windows Vista and later. Windows XP is not supported.

Veles Core should also work on most other Unix-like systems but is not
frequently tested on them.

0.18.1.3 change log
===================

New RPC's: 
----------

 - `privatesend` - use for stop , start or restart PrivateSend mixing 

 - `setprivatesendamount` - use for set the goal amount in Veles for PrivateSend mixing 

 - `setprivatesendrounds` - use for set the number of rounds for PrivateSend mixing

Update RPC's: 
-------------

 - `getwalletinfo` - add 'privatesend_balance' into output of command 


Activation and Introduction PrivateSend
---------------------------------------

PrivateSend is disabled by default ,to activate PrivateSend function open your Veles Core wallet, go to Settings and select Options. It will only start after you set the number of rounds and number of Veles to mix under settings and click Start Mixing on the Overview tab of your wallet.

NOTE: To prevent system abuse, an average of one in ten rounds of masternode mixing incurs a fee of .0001 VLS.

Enter a target value for Amount of VLS to keep anonymized. This value provides a lower boundary on the final amount of funds to be anonymized. Depending on how the client splits your wallet balance, you may end up with denominated inputs whose sum total is greater than the target amount. In this case the client will use all existing denominated inputs in the PrivateSend process. The final anonymized amount may be higher than your target, but should be close.

Starting Mixing
---------------

The PrivateSend process is initiated by clicking the Start Mixing button on the Overview tab of the Veles Core wallet. Mixing is possible once the following conditions have been met:

 The wallet contains sufficient non-anonymized funds to create the minimum required denominated values
 The user has not disabled PrivateSend in the Options dialog
 The target value for anonymized Funds in the Options dialog is greater than zero

If your wallet is encrypted (highly recommended), you will be asked to enter your wallet passphrase. Enable the Only for mixing via PrivateSend checkbox to unlock the wallet for mixing only.This will unlock your wallet, and the PrivateSend mixing process will begin. The wallet will remain unlocked until PrivateSend mixing is complete, at which point it will be locked automatically.

PrivateSend will begin creating transactions and your PrivateSend balance will gradually increase. This process can take some time, so be patient. You can monitor the process in more detail as described in the following section.

Any of the following actions will interrupt the mixing process. Because the transactions are atomic (they either take place completely, or do not take place at all), it should be possible to safely interrupt PrivateSend mixing at any time.

 Clicking the Stop Mixing button on the Overview tab
 Closing the client before PrivateSend mixing is completed
 Sending PrivateSend funds from the wallet before PrivateSend rounds are completed
 Disabling PrivateSend before the process is complete

Monitoring Mixing
-----------------

If you want to monitor PrivateSend in more detail, you need to enable some advanced features of the wallet. Go to Settings, select Options and go to the Wallet tab. Check the boxes next to the Enable coin control features and Enable advanced PrivateSend interface options.

Since PrivateSend mixing creates a lot of new address keys to send and receive the anonymized denominations, you may receive a warning when the number of remaining keys runs low. This is nothing to be worried about, since the wallet will simply create more keys as necessary. However, these keys will not exist in any previous backups of your wallet. For this reason, it is important to backup your wallet again after mixing is complete.

You can also monitor PrivateSend progress by viewing the transactions created by the mixing process on the Transactions tab.
The following table describes the PrivateSend-related transactions displayed in the Type column of the Transactions tab:

 PrivateSend Make Collateral Inputs(Mixing)- Wallet funds were moved to collateral inputs that will be used to make collateral payments. This is done to minimize traceability of collaterals.

 PrivateSend Create Denominations(Mixing)- Wallet funds were broken into PrivateSend denominations (Step 1 here)

 PrivateSend Denominate(Mixing)- A transaction was sent to a masternode in order to participate in a mixing session (Step 3 here)

 PrivateSend Collateral Payment(Mixing)- The mixing session collateral was claimed. This fee is charged in ~10% of mixing sessions to prevent spam attacks.

 PrivateSend (Spending)-	Mixed funds were used to send a payment to someone. Note: Unlike the previous 4 transaction types, this is not a mixing process transaction.

You can also use the coin control feature to view which addresses hold mixed denominations ready to be used for PrivateSend transactions. Go to the Send tab of your wallet and click Inputs to view the possible input addresses for your transactions. You can see how each address holds given denominations of mixed Veles, and how many rounds of mixing have been completed. This is to ensure that an efficient combination of addresses can be used as inputs in PrivateSend transactions without too much change, since amount in a PrivateSend transaction must be rounded up to completely spend all inputs. The current minimum balance for an input used in a PrivateSend transaction is 0.00100010 VLS.
Coin Selection dialog showing addresses holding PrivateSend mixed balances in different denominations

Paying with PrivateSend
-----------------------

You can only use PrivateSend for payments once you have mixed enough VLS to make up the amount you are trying to send. Because the mixing process takes time, it must be done in advance before you create the send transaction. A PrivateSend transaction is effectively the same as any other transaction on the blockchain, but it draws only from input addresses where the denomination has previously been mixed to ensure anonymity of funds. Because several input addresses are usually required to make up the amount you are trying to send, a PrivateSend transaction will usually take up more space (in kilobytes) on the blockchain, and therefore will be charged a slightly higher fee.

To send a payment using PrivateSend, go to the Send tab of the Veles Core wallet and enable the PrivateSend option. The balance displayed will change to show your PrivateSend balance instead of the total balance. You can then enter the Pay To address, Label, Amount and click Send as usual. Your payment will be rounded up to completely spend the lowest possible denomination of mixed balance available (currently to the nearest 0.001 VLS). You will be prompted to enter your password and receive a detailed breakdown of the fee structure for PrivateSend before sending.

Credits
=======

Thanks to everyone who directly contributed to this release:

- AltcoinBaggins
- Barrystyle
- mdfkbtc
- UhlikSK

Special thanks to whole Dash Core team !

As well as everyone that helped to improve Veles Core with their suggestions at [Veles Discord](https://discord.gg/rXgH6Qn).
