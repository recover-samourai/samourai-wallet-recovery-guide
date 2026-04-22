# Samourai Wallet Not Syncing: Complete Fix Guide

If you opened your old Samourai Wallet in 2026 and saw the dreaded "Connecting..." spinner that never finishes, or a zero balance, or an endless transaction history load - here is the honest answer. The app will never sync again. The backend it depended on was seized in April 2024 and is not coming back. But your Bitcoin is fine, and the fix is straightforward. This article covers both the "why" and the practical recovery workflow. The companion [not-syncing fix blog article](https://samourai-wallet.io/blog/samourai-wallet-not-syncing-fix-guide) covers additional edge cases.

## Why the app does not sync

Samourai Wallet was designed to talk to Samourai-operated infrastructure - a backend service called Dojo (which users could self-host) and the Whirlpool coordinator. When the Department of Justice seized that infrastructure in April 2024, every hosted endpoint stopped responding. A mobile wallet with no reachable server cannot fetch blockchain data, and without blockchain data it cannot show your balance or any transactions.

Self-hosted Dojo users had a longer runway - their own backend kept running - but the Whirlpool coordinator was centralized, so mixing stopped regardless. Today, even self-hosted Dojo users are better served recovering into a modern wallet than maintaining an unsupported app. The [Samourai Wallet 2026 status](https://samourai-wallet.io/) page has the full context.

## What you should not do

- Do not reinstall the APK from a mirror. The backend is gone; reinstalling will not help. APK mirrors in 2026 are exclusively phishing traps.
- Do not factory reset your phone with the app still installed. If your seed backup is flaky, this can be a one-way trip. Recover first, reset later.
- Do not type your seed into a website that promises to "sync" or "check" your wallet. Every such site is a scam.
- Do not pay anyone to recover your wallet. Recovery is free, and the people who charge for it are always thieves.

## What to do instead

Recover the seed into a desktop wallet that still works in 2026. This takes about thirty minutes.

### 1. Get your seed phrase

The 12-word seed is what controls your Bitcoin. The app is just a viewer. If you have the seed, you have the money. If you wrote down the seed on paper, now is the moment you are glad you did.

If you used a BIP39 passphrase (a second password on top of the 12 words), you need that too. Without it, funds hidden behind the passphrase are unrecoverable. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) has a whole section on passphrase detection.

### 2. Install Sparrow or Electrum

Go to the [verified download hub](https://samourai-wallet.io/samourai-wallet-download-apk). Sparrow is the recommended choice for Samourai recovery; Electrum is the fallback. The [Sparrow Wallet review](https://samourai-wallet.io/sparrow-wallet-review) covers why, and [Samourai Wallet vs Electrum](https://samourai-wallet.io/samourai-wallet-vs-electrum) covers the tradeoffs.

### 3. Import your seed

In Sparrow: File > New Wallet > name it > Script Type P2WPKH > Keystore "Use 12 Word Seed" > paste seed > enter passphrase if used > Apply.

In Electrum: File > New > Standard wallet > I already have a seed > paste > Options > BIP39 > derivation `m/84'/0'/0'`.

The [30-minute recovery guide](https://samourai-wallet.io/recover-samourai-wallet-funds) is the detailed version.

### 4. Add Whirlpool accounts if you mixed

Anyone who ever used Whirlpool needs to add the non-standard derivation paths: `m/84'/0'/2147483644'` (bad bank), `2147483645'` (premix), `2147483646'` (postmix), `2147483647'` (Ricochet). The [Whirlpool UTXO recovery guide](https://samourai-wallet.io/whirlpool-utxo-recovery-guide) is the definitive explanation.

### 5. Verify and decide

Add up the balances. That is your full Samourai holding. From there you either keep the recovered seed as your ongoing wallet or consolidate into a fresh one. The [Sparrow migration guide](https://samourai-wallet.io/samourai-wallet-to-sparrow-migration) covers both paths.

## "But the app showed a balance yesterday"

Some users report that the app occasionally loads a cached balance from months ago, then re-hangs. The cached values are exactly that - cached. They do not reflect current UTXO state. Current state only comes from querying the blockchain, which the app cannot do because its endpoints are gone. Ignore what the app shows and recover via a working wallet.

## "I self-hosted Dojo - does that help"

A self-hosted Dojo still works insofar as it talks to Bitcoin Core. You can technically keep using Samourai Wallet against your own Dojo until the app itself breaks on a new phone or OS update. In practice, this is a dead end: the app is unmaintained, new Android versions will eventually break it, and the Whirlpool coordinator is gone regardless. Move to Sparrow. Your Dojo can still sit in front of Bitcoin Core and serve Sparrow instead - same full-node privacy, actively maintained frontend.

## "Can I recover from the APK file itself"

No. The APK is an application binary. The keys live in the phone's encrypted wallet file, which you cannot meaningfully extract without the app running. If you have a backup export file from inside Samourai - yes, that helps, especially for Whirlpool UTXO identification - but the seed phrase alone is sufficient for full recovery. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) has more detail.

## What happened to the servers

The [DOJ case timeline](https://samourai-wallet.io/samourai-wallet-doj-case-timeline) covers the seizure in detail. The short version: the servers are evidence in a federal prosecution. They are not coming back. That is settled.

## Final warning

Three things, once more.

- Never type your seed into a website.
- Never pay anyone to recover your wallet.
- Never download Samourai APKs from random mirrors.

The [best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) page is your next stop for picking where to land after recovery.

## Related articles

- [Recover Samourai Wallet BTC in 30 Minutes](recover-samourai-wallet-btc-30-minutes.md)
- [Samourai to Sparrow Wallet Migration Guide](samourai-to-sparrow-migration.md)
- [Samourai Electrum Recovery - The Legacy Fallback Method](samourai-electrum-recovery-legacy.md)
- [Samourai Wallet Backup Strategies 2026](samourai-wallet-backup-strategies-2026.md)
