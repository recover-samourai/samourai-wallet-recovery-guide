# Finding Whirlpool UTXOs with Hidden Derivation Paths

The single most common "lost Bitcoin" story from former Samourai users goes like this: seed imported correctly, passphrase entered, main balance shows up, total is wrong. The missing coins are almost always sitting in a Whirlpool account on a derivation path the import never checked.

This article explains why Samourai designed Whirlpool that way, how to list every account that could possibly contain your UTXOs, and how to surface them in Sparrow or Electrum. For a guided import flow, the [Whirlpool UTXO recovery guide](https://samourai-wallet.io/whirlpool-utxo-recovery-guide) is the canonical walkthrough.

## Why Whirlpool uses non-standard accounts

BIP84 defines native SegWit accounts starting at `m/84'/0'/0'`. Most wallets stop there. Samourai wanted the Whirlpool mixing flow - premix intake, bad bank change, postmix outputs - to stay cleanly separate from a user's everyday deposit address set. The solution was a fixed set of high account indexes that a naive `m/84'/0'/*'` scan would never reach.

These are the exact values Samourai used internally:

| Account      | Derivation path                | What lives there                               |
|--------------|--------------------------------|------------------------------------------------|
| Deposit      | `m/84'/0'/0'`                  | Addresses you received BTC on                  |
| Bad Bank     | `m/84'/0'/2147483644'`         | Change from the tx0 that seeded the mix       |
| Premix       | `m/84'/0'/2147483645'`         | UTXOs queued for mixing                        |
| Postmix      | `m/84'/0'/2147483646'`         | Mixed outputs - usually the largest balance    |
| Ricochet     | `m/84'/0'/2147483647'`         | Hop transactions used for extra privacy        |

The high indexes are deliberate. `2147483647` is the maximum hardened account index that BIP32 allows, so Samourai counted down from there. It is not random, it is not arbitrary, and no amount of scrolling through a normal wallet's account list will find them by accident. They must be added explicitly.

## Step one: Rule out the obvious

Before assuming you have missing Whirlpool funds, confirm the basics. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) covers the top false alarms: wrong passphrase, missing BIP39 passphrase field, wrong script type, unconfirmed Electrum wallets pointed at a non-functional server. If none of those apply and your total is still light, move to the Whirlpool accounts.

Starting from a working main import is easier, so if you have not done the default import yet, follow the [30-minute recovery guide](https://samourai-wallet.io/recover-samourai-wallet-funds) first and come back here.

## Step two: Add each Whirlpool account in Sparrow

Sparrow Wallet treats every derivation path as a separate wallet. That sounds tedious but it is clean: balances stay isolated, you can spend from each account independently, and you can see which pool your mixed coins came from.

1. File > New Wallet > name it "Samourai Postmix"
2. Script Type: "Native SegWit (P2WPKH)"
3. Keystore > "Use 12 Word Seed"
4. Paste the seed, add the passphrase if you had one
5. In the Keystore tab, edit the Derivation field to `m/84'/0'/2147483646'`
6. Apply

Sparrow will scan that account and - if you ever mixed anything - show the postmix UTXOs. Repeat the same process for `2147483645'` (premix), `2147483644'` (bad bank) and `2147483647'` (Ricochet).

The [Samourai to Sparrow migration guide](https://samourai-wallet.io/samourai-wallet-to-sparrow-migration) shows this same procedure using Sparrow's multi-account workflow, which is cleaner if you have multiple accounts to import.

## Step three: Electrum equivalent

Electrum handles this less elegantly. You need one wallet file per account. File > New > Standard wallet > I already have a seed > paste > Options > BIP39, then for derivation path enter `m/84'/0'/2147483646'` for postmix. Save as "samourai-postmix.dat." Repeat for each account with a different filename. The [Electrum recovery guide](https://samourai-wallet.io/samourai-wallet-electrum-recovery) has screenshots.

Electrum is also slower because each wallet scan queries a public server. If you are recovering a lot of accounts, prefer Sparrow.

## Step four: Verify and consolidate

Total up all account balances. That number is your full pre-seizure Samourai holding. If you plan to keep the funds together going forward, create a single fresh wallet (new seed, new backup) and send from each account to a deposit address in the new wallet. The [best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) page lists good candidate destinations, and the [Sparrow Wallet review](https://samourai-wallet.io/sparrow-wallet-review) covers using Sparrow itself as your new main wallet.

## Privacy warning about consolidating

The whole point of Whirlpool was keeping pre-mix and post-mix coins unlinkable. Sending them into a single new wallet undoes that. If privacy matters to you, keep the postmix outputs separate from any KYC-linked address and consider continuing to mix with a current-generation coordinator. The [Wasabi Wallet review](https://samourai-wallet.io/wasabi-wallet-review) compares the main still-active CoinJoin option in 2026.

## What if a path returns nothing

An empty scan on `2147483646'` means one of three things: you never mixed, the passphrase is wrong, or the seed is mis-typed. Mis-typing shows up as an empty main wallet too, which is a useful sanity check. A correct passphrase plus a never-used Whirlpool account is perfectly normal - most Samourai users never mixed.

## Related articles

- [Recover Samourai Wallet BTC in 30 Minutes](recover-samourai-wallet-btc-30-minutes.md)
- [Samourai to Sparrow Wallet Migration Guide](samourai-to-sparrow-migration.md)
- [Samourai Wallet Not Syncing - Complete Fix Guide](samourai-wallet-not-syncing-fix.md)
- [Samourai Wallet Backup Strategies 2026](samourai-wallet-backup-strategies-2026.md)
