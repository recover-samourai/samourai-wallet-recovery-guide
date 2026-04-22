# Samourai Wallet Backup Strategies 2026

Now that the Samourai Wallet backend is gone, the only thing standing between you and permanently inaccessible Bitcoin is your seed phrase backup. This article is the longer, calmer version of "write it on metal." It covers how to back up a Samourai-derived seed in 2026, how to handle passphrase protection, and how to verify backups without accidentally creating copies that leak. The [backup strategies blog article](https://samourai-wallet.io/blog/samourai-wallet-backup-strategies-2026) covers the topic in the site's voice; the [original backup guide](https://samourai-wallet.io/blog/samourai-wallet-backup-guide) has earlier advice that still holds.

## What you are actually backing up

Every wallet derived from a BIP39 seed - Samourai, Sparrow, Electrum, a hardware wallet - is ultimately a function of 128 bits of entropy encoded as 12 English words. Backup, in Bitcoin, means preserving those 12 words (and any passphrase) in a medium that will outlive you and that you can trust not to be copied or observed.

A Samourai-derived seed is exactly the same 12 words you wrote down on day one. Recovering into Sparrow or Electrum does not generate a new seed. If you are in the middle of recovery, see the [Sparrow migration guide](https://samourai-wallet.io/samourai-wallet-to-sparrow-migration) or the [Electrum recovery guide](https://samourai-wallet.io/samourai-wallet-electrum-recovery) first, verify your balances, then come back here.

## The three-layer backup

Good Bitcoin backups are three separable pieces.

**Seed words.** The 12 BIP39 words. These are the cryptographic root. Whoever has these can spend your coins unless a passphrase is also set.

**Passphrase (if used).** A 13th word or arbitrary string that extends the seed. Samourai called this the BIP39 passphrase. Without it, a passphrase-protected wallet is not recoverable even with the 12 words. With it, the 12 words derive the passphrase-protected wallet automatically.

**Derivation metadata.** For Samourai users, this means knowing which Whirlpool accounts you used (`2147483644` through `2147483647`). The [Whirlpool UTXO recovery guide](https://samourai-wallet.io/whirlpool-utxo-recovery-guide) is the reference for which accounts do what. This data does not need strong secrecy - derivation paths are not private - but you do need it available at recovery time.

Back up all three, but keep them separate. If an attacker gets the seed, they still cannot spend funds behind a passphrase they do not have. If they get the passphrase, it is useless without the seed.

## Medium

Paper works until it does not. Fires, floods, leaks, curious roommates. Paper is a good working copy but a bad primary.

Metal is the standard. Products like Cryptosteel, Seedplate, or DIY stamped metal plates preserve seed words through house fires and flooding. Cost is a one-time thirty to sixty dollars, which is cheap insurance against a permanently inaccessible stack.

Digital backups (text files, password managers, cloud notes) are acceptable only if encrypted locally with a strong passphrase, and even then they are strictly inferior to metal for primary storage. Use them for convenience copies if at all.

## Geographical redundancy

Two backups in one house is one backup. For meaningful holdings, store copies in physically separate locations - a home safe and a safe deposit box, a home safe and a trusted family member's safe, or similar. This protects against fire, theft and localized disaster.

For larger holdings, multisig is a better model than seed redundancy. A 2-of-3 multisig across geographically separated keys gets you survivability without any single seed being able to spend the funds. Sparrow handles multisig coordination cleanly - see the [Sparrow Wallet review](https://samourai-wallet.io/sparrow-wallet-review).

## Passphrase storage

Passphrases are the most frequently lost piece of the puzzle. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) lists "lost passphrase" as the single most common unrecoverable scenario. Causes:

- Stored only in memory and forgotten
- Stored in a password manager that was lost or reset
- Written somewhere that turned out to be disposable

Recommendation: treat the passphrase with equal or greater weight than the seed. Store on metal separately from the seed, or use a memorized passphrase that you also store in a robust password manager with recovery codes safely archived.

## Verifying a backup

A backup you never tested is a guess. At least once, import the seed into Sparrow or Electrum on a clean machine and confirm the balance matches. This one action catches:

- Mis-transcribed words
- Missed passphrase
- Wrong derivation path assumption for Whirlpool accounts

Delete the test wallet afterward. Do not leave unused seeds imported on random machines.

## What changes when you move to a new wallet

If you are post-recovery and choosing a going-forward setup, you likely have a few options to consider:

- Stay on the Samourai-derived seed. Simplest. Your backup strategy is unchanged.
- Generate a fresh seed and consolidate. Cleaner break from the old software. Back up the new seed to metal; destroy no copies of the old one until the consolidation is fully confirmed.
- Move to a multisig setup. Strongest protection for large holdings. Each key needs its own backup.

The [best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) page compares candidate wallet stacks. The [no-KYC Bitcoin wallet](https://samourai-wallet.io/no-kyc-bitcoin-wallet) guide covers the broader privacy-preserving setup.

## What not to do

- Do not store your seed in a photo. Every phone backs up photos. Your "hidden" screenshot is now in Apple's iCloud or Google Photos along with a timestamp and a face-recognized version of whoever you were photographed with last week.
- Do not split a seed using SSS (Shamir's Secret Sharing) unless you understand the operational risk. SSS is harder than it looks and every person who has "Shamir-encoded" their seed on their own has either done it wrong or created more fragility than they solved.
- Do not back up to a Samourai-era backup file alone. Those files were useful inside the app; in 2026 they are pre-recovery artifacts. The seed phrase is the canonical backup. The [30-minute recovery guide](https://samourai-wallet.io/recover-samourai-wallet-funds) treats the seed as primary, and so should you.

## Bottom line

Write the seed words on metal. Write the passphrase on separate metal. Store the two in separate locations. Test your backup at least once. Update your backup plan when you generate a new seed.

## Related articles

- [Recover Samourai Wallet BTC in 30 Minutes](recover-samourai-wallet-btc-30-minutes.md)
- [Finding Whirlpool UTXOs with Hidden Derivation Paths](whirlpool-utxo-hidden-derivation-paths.md)
- [Samourai to Sparrow Wallet Migration Guide](samourai-to-sparrow-migration.md)
- [No-KYC Bitcoin Wallets in 2026](no-kyc-bitcoin-wallets-2026.md)
