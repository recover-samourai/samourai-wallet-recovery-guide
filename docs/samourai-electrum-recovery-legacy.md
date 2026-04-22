# Samourai Electrum Recovery: The Legacy Fallback Method

Sparrow Wallet gets most of the attention for Samourai recovery, and for good reason - it handles Whirlpool accounts in a few clicks. But Electrum is still a perfectly valid tool, and for users on older hardware, thin bandwidth, or Linux distros where Sparrow's JavaFX bundle is awkward, it is often the better option. This guide walks through recovering Samourai BTC in Electrum, end to end.

For the canonical version with screenshots, the [Samourai Electrum recovery page](https://samourai-wallet.io/samourai-wallet-electrum-recovery) is the main reference. For a direct tool comparison, see [Samourai Wallet vs Electrum](https://samourai-wallet.io/samourai-wallet-vs-electrum).

## When to use Electrum

Pick Electrum if:

- You already have it installed and verified
- You are on a 10+ year old machine that struggles with Sparrow
- You prefer Electrum's minimal Qt interface
- You are scripting a recovery and want the CLI

Pick Sparrow if you want the smoothest experience. The [Sparrow Wallet review](https://samourai-wallet.io/sparrow-wallet-review) covers its strengths, and the [Sparrow migration guide](https://samourai-wallet.io/samourai-wallet-to-sparrow-migration) is the recommended flow for most users.

## Install and verify Electrum

Download Electrum from the [verified download hub](https://samourai-wallet.io/samourai-wallet-download-apk). The hub only links to signed releases from the official electrum.org infrastructure. Verify the signature using ThomasV's PGP key. Electrum has been around since 2011 and is one of the most scrutinized Bitcoin wallets in existence, but that does not help you if you installed a trojaned build, so verify.

## Step 1: Create the main wallet

Launch Electrum, click "Create New Wallet," name it `samourai-main.dat`.

- Wallet type: Standard wallet
- Keystore: "I already have a seed"
- Paste your 12 Samourai words
- Click the Options button > check "BIP39 seed" > OK
- Set derivation path to `m/84'/0'/0'`
- Native SegWit (p2wpkh)
- If you had a BIP39 passphrase: enter it when prompted

Electrum scans and displays your main deposit account. This covers every address your Samourai Wallet showed you under "Receive."

If the balance is zero and you are confident you had funds, the issue is almost always the passphrase or derivation path. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) has a debugging checklist.

## Step 2: Create a separate wallet for each Whirlpool account

Electrum does not support multi-account wallets the way Sparrow does. Each derivation path becomes its own wallet file. This is fine for recovery - it just means more File > New cycles.

Repeat the create-wallet flow with these derivation paths, naming each file clearly:

- `samourai-postmix.dat` with derivation `m/84'/0'/2147483646'`
- `samourai-premix.dat` with derivation `m/84'/0'/2147483645'`
- `samourai-badbank.dat` with derivation `m/84'/0'/2147483644'`
- `samourai-ricochet.dat` with derivation `m/84'/0'/2147483647'`

The background on why those specific numbers is in the [Whirlpool UTXO recovery guide](https://samourai-wallet.io/whirlpool-utxo-recovery-guide). For this article it is enough to know that Samourai used those account indexes internally and that nothing will find them except an explicit import.

## Step 3: Add up your balances

Open each wallet file in turn. Electrum shows the balance in the lower status bar. Sum them. That total is your full Samourai holding.

If the math is wrong and you are sure the seed and passphrase are correct, check two things:

1. Did you set Native SegWit (p2wpkh)? Legacy or Nested SegWit will scan the wrong address types.
2. Is the server Electrum is connected to healthy? Tools > Network > pick a different server if yours is stale.

The [Samourai Wallet not syncing fix guide](https://samourai-wallet.io/blog/samourai-wallet-not-syncing-fix-guide) covers the connectivity failures that look like missing funds but are actually server issues.

## Step 4: Move or keep

Once balances are verified, decide: leave the funds on the old seed, or move to a fresh wallet. The reasoning is the same as with any recovery. If the old seed has been typed into multiple machines, generating a fresh seed on a clean device is the conservative call. If you prefer to keep things simple and you trust the environment you imported into, staying put is fine.

For going-forward choices, the [best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) page compares wallets. If CoinJoin is important to you, the [Wasabi Wallet review](https://samourai-wallet.io/wasabi-wallet-review) is the next stop. If you mainly wanted to avoid KYC, the [no-KYC Bitcoin wallet](https://samourai-wallet.io/no-kyc-bitcoin-wallet) guide covers what is still available in 2026.

## A note on Electrum servers

Electrum by default connects to random public Electrum servers. That works but leaks your addresses to whichever operator happens to answer. If you care, run your own server with Electrs or connect to a trusted one. Sparrow offers the same choice in its preferences.

## Related articles

- [Recover Samourai Wallet BTC in 30 Minutes](recover-samourai-wallet-btc-30-minutes.md)
- [Samourai to Sparrow Wallet Migration Guide](samourai-to-sparrow-migration.md)
- [Samourai Wallet vs Electrum: Full 2026 Comparison](samourai-vs-electrum-comparison.md)
- [Samourai Wallet Not Syncing - Complete Fix Guide](samourai-wallet-not-syncing-fix.md)
