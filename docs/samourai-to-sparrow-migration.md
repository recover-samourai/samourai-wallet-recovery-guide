# Samourai to Sparrow Wallet Migration Guide

Sparrow Wallet is the cleanest way to leave Samourai behind. It supports BIP39 seeds with passphrases, handles custom derivation paths without ceremony, and lets you run multiple accounts under one wallet file - which matters for anyone recovering Whirlpool UTXOs. This guide walks through a full migration in one sitting. For the canonical step-by-step version, the [Samourai to Sparrow migration page](https://samourai-wallet.io/samourai-wallet-to-sparrow-migration) is the primary reference.

## Why Sparrow and not something else

Sparrow is an open-source Bitcoin-only desktop wallet written by Craig Raw. It reads standard BIP39 seed phrases, supports native SegWit natively, integrates hardware wallets, and exposes every derivation path the UI needs. The [Sparrow Wallet review](https://samourai-wallet.io/sparrow-wallet-review) covers the full feature surface. For the specific purpose of recovering a Samourai seed with all its Whirlpool accounts, nothing else comes close.

Electrum will also work but is less ergonomic for multi-account recovery. See [Samourai Wallet vs Electrum](https://samourai-wallet.io/samourai-wallet-vs-electrum) and the [Electrum recovery guide](https://samourai-wallet.io/samourai-wallet-electrum-recovery) for the fallback flow.

## Prerequisites

- Your 12-word seed phrase
- Your BIP39 passphrase if you used one (you would remember typing a second password in Samourai if so)
- A desktop computer running Windows, macOS or Linux
- Sparrow Wallet installed from the [verified download hub](https://samourai-wallet.io/samourai-wallet-download-apk)

If you cannot find one of those items, read the [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) before going further. Some cases are solvable, others are not, and it is worth knowing which camp you are in before you start.

## Step 1: Install and verify Sparrow

Download the signed installer from the download hub. Sparrow publishes PGP signatures and SHA-256 hashes for every release. Verify the hash against the value published on the site. It takes ninety seconds and rules out tampered installers.

On first launch, Sparrow asks which network and which connection type. Leave "Bitcoin mainnet" selected. For connection, the default "Public Electrum" works but leaks your addresses to a public server. If you run a full node, use "Bitcoin Core" instead. For a one-off recovery, public Electrum is acceptable as long as you do not plan to keep large balances there long term.

## Step 2: Create the main deposit wallet

File > New Wallet. Name it "Samourai Deposit." Keep Policy Type "Single Signature" and Script Type "Native SegWit (P2WPKH)." Open the Keystore tab, click "Use 12 Word Seed," paste your words, enter your passphrase in the Passphrase field if you had one, and click Import Keystore > Apply.

Sparrow will show the wallet with derivation path `m/84'/0'/0'`. This is the main deposit account. Give it a minute to scan and your main balance should appear.

## Step 3: Add the Whirlpool accounts

Here is where Sparrow earns its keep. For each Whirlpool account, repeat the new-wallet flow but change the derivation path:

- "Samourai Postmix" > derivation `m/84'/0'/2147483646'`
- "Samourai Premix" > derivation `m/84'/0'/2147483645'`
- "Samourai Bad Bank" > derivation `m/84'/0'/2147483644'`
- "Samourai Ricochet" > derivation `m/84'/0'/2147483647'`

The [Whirlpool UTXO recovery guide](https://samourai-wallet.io/whirlpool-utxo-recovery-guide) explains the reasoning behind those exact indexes. Only add the accounts you might actually have used - if you never clicked the Whirlpool button, postmix will be empty and the others are irrelevant.

## Step 4: Verify balances

With all your Samourai-derived wallets open in Sparrow, open each one in turn and note the balance. Add them up. That is your full historical Samourai holding.

If the total is off and you are sure every account is imported, the [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) lists the most common causes - wrong passphrase, change address not yet scanned, or UTXOs that moved before the seizure. In practice, ninety percent of "missing balance" reports come down to the passphrase field being empty when it should not be.

## Step 5: Decide whether to migrate or consolidate

You have two reasonable paths from here:

**Keep the old seed, use Sparrow as your new wallet.** Simple, but the seed has been typed into multiple machines over the years. If that worries you, move on.

**Generate a fresh seed and consolidate.** Create a brand new wallet in Sparrow (Tools > Generate) or on a hardware wallet. Back up the new seed on metal. Send from each Samourai-derived account to addresses in the new wallet. Caveat: consolidating Whirlpool postmix coins with other coins undoes the privacy you paid fees for. If the mixed coins matter, keep them on their own fresh seed.

The [best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) page compares wallet options for going forward. For a look at the closest continued CoinJoin coordinator, the [Wasabi Wallet review](https://samourai-wallet.io/wasabi-wallet-review) covers the main active alternative in 2026.

## Common Sparrow gotchas

- "Script Type mismatch" usually means you picked Legacy or Nested SegWit. Samourai was Native SegWit. Use P2WPKH.
- Empty balance after successful import: the wallet is still syncing. Wait for the blockchain tip counter at the bottom of the screen to catch up, or switch the server connection.
- "Expected server response did not arrive": your Electrum server is flaky. Change it under File > Preferences > Server.

## Related articles

- [Recover Samourai Wallet BTC in 30 Minutes](recover-samourai-wallet-btc-30-minutes.md)
- [Finding Whirlpool UTXOs with Hidden Derivation Paths](whirlpool-utxo-hidden-derivation-paths.md)
- [Samourai Electrum Recovery - The Legacy Fallback Method](samourai-electrum-recovery-legacy.md)
- [Best Samourai Wallet Alternatives in 2026](best-samourai-wallet-alternatives-2026.md)
