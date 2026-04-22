# Recover Samourai Wallet BTC in 30 Minutes

This is the short version. If you have your 12-word seed phrase and a computer running Windows, macOS or Linux, you can recover every Bitcoin in your Samourai Wallet in under thirty minutes. This guide lays out the entire flow as a checklist. For deeper context on each step, the [complete recovery walkthrough](https://samourai-wallet.io/recover-samourai-wallet-funds) goes phase by phase.

## Before the clock starts

Find your seed phrase. It will be a list of 12 English words, almost always on a piece of paper or a metal backup plate. If you used a passphrase on top of the seed - Samourai called it a BIP39 passphrase - you also need that exact string. Passphrase-protected wallets without the passphrase are unrecoverable. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) covers what to try if you are not sure whether you used one.

Unplug your phone if the old Samourai Wallet is still installed. You do not need it. Recovery happens on a desktop.

## Minute 0 to 5: Install a recovery wallet

Go to the [verified download hub](https://samourai-wallet.io/samourai-wallet-download-apk) and download either Sparrow Wallet or Electrum. Sparrow is the modern choice and the one we recommend - it handles Whirlpool UTXOs natively. Electrum is the legacy fallback for older computers or users who want a minimal UI. Both are fine. See [Samourai Wallet vs Electrum](https://samourai-wallet.io/samourai-wallet-vs-electrum) and the [Sparrow Wallet review](https://samourai-wallet.io/sparrow-wallet-review) if you want to choose deliberately.

Install, launch, and let it finish its initial connection to the Bitcoin network.

## Minute 5 to 15: Import your seed

In Sparrow: File > New Wallet > name it something you will recognize > Script Type "Native SegWit (P2WPKH)" > Keystore "Use 12 Word Seed". Paste your 12 words, add your passphrase in the Passphrase field if you used one, and click Import Keystore > Apply. Sparrow will show the main account at derivation path `m/84'/0'/0'`.

In Electrum: File > New > Standard wallet > I already have a seed > paste the 12 words > Options > BIP39 seed, then enter the derivation path `m/84'/0'/0'`. The [Electrum recovery guide](https://samourai-wallet.io/samourai-wallet-electrum-recovery) has the exact menu sequence with screenshots.

Within a minute or two, your main wallet balance should appear. If the only funds you ever had were in the default deposit account, you are done. Skip to minute 25.

## Minute 15 to 25: Recover Whirlpool and Ricochet accounts

If you ever used Whirlpool CoinJoin or Ricochet, the main import will not surface those UTXOs. They live at non-standard account indexes that Samourai used internally. In Sparrow, File > New Wallet, repeat the import, but set the account number manually. The four paths you may need:

- Deposit: `m/84'/0'/0'` - covered by the default import
- Bad Bank: `m/84'/0'/2147483644'` - change from Whirlpool tx0
- Premix: `m/84'/0'/2147483645'` - UTXOs queued for mixing
- Postmix: `m/84'/0'/2147483646'` - mixed outputs, the important one
- Ricochet: `m/84'/0'/2147483647'` - hop transactions

Each account becomes a separate wallet in Sparrow. The [Whirlpool UTXO recovery guide](https://samourai-wallet.io/whirlpool-utxo-recovery-guide) explains why these specific indexes and how to spot UTXOs that landed on unexpected paths. If you migrate instead of importing account by account, the [Sparrow migration guide](https://samourai-wallet.io/samourai-wallet-to-sparrow-migration) walks through Sparrow's multi-account import in one pass.

## Minute 25 to 30: Verify and plan next steps

Total up the balances across every account. That is your full Samourai Wallet balance. If the total looks wrong - lower than you expected - do not panic. Common causes: you imported without the passphrase, you forgot about a Whirlpool account, or a child address is still missing. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) has a troubleshooting checklist.

Once the total matches your memory, decide what to do next. You can leave the funds on the recovered seed and treat Sparrow as your new primary wallet. Or you can generate a fresh seed and consolidate everything into it, which is the cleaner option if you suspect your old seed may have been exposed. The [best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) page compares the main options for a forward-looking wallet.

## Warnings, again

Every recovery guide repeats these, and every month new users still fall for the scams they describe.

- Never type your seed phrase into a website. Ever. Recovery tools are always local applications.
- Never pay a recovery service. Anyone asking for payment to recover a self-custody wallet is stealing your coins.
- Never download Samourai Wallet APKs from random mirrors. The mobile app cannot recover itself because the backend is gone. APK mirrors in 2026 are exclusively phishing traps. Stick to the [official download hub](https://samourai-wallet.io/samourai-wallet-download-apk).

## Related articles

- [Samourai Wallet 2026 Status](samourai-wallet-2026-status.md)
- [Finding Whirlpool UTXOs with Hidden Derivation Paths](whirlpool-utxo-hidden-derivation-paths.md)
- [Samourai to Sparrow Wallet Migration Guide](samourai-to-sparrow-migration.md)
- [Samourai Electrum Recovery - The Legacy Fallback Method](samourai-electrum-recovery-legacy.md)
