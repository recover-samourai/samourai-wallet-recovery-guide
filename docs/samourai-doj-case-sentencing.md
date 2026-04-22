# Samourai Wallet DOJ Case Timeline and Sentencing

The Samourai Wallet case is the most consequential privacy-tool prosecution of the decade. This article lays out the public timeline, the charges, and the 2025 sentencing - and separates what the case changed operationally from what it did not change for end users. For the full document-by-document record, the [DOJ case timeline](https://samourai-wallet.io/samourai-wallet-doj-case-timeline) is the canonical source. The [sentencing update](https://samourai-wallet.io/samourai-wallet-sentencing-update) covers the 2025 outcome in detail.

## April 2024: the arrests and seizure

On April 24, 2024, the FBI arrested Keonne Rodriguez in New York and Samourai co-founder William Hill in Portugal on a US warrant. The same morning, the Department of Justice unsealed an indictment in the Southern District of New York charging both with conspiracy to commit money laundering and operating an unlicensed money transmitting business. The indictment referenced roughly 100 million US dollars in allegedly laundered funds moved through Samourai's Whirlpool coordinator over an approximately nine-year operational window.

The operational effects were immediate. Samourai's servers were seized, the mobile app was removed from Google Play, and the official samouraiwallet.com site was replaced with a DOJ notice. Users who opened the app saw a zero balance and assumed their BTC was gone. It was not. Self-custody wallets store keys on the user's device, and the seized infrastructure was a backend, not a custodian.

## Mid-2024: pretrial proceedings

Rodriguez was released on bond in May 2024 after posting a multi-million-dollar package. Hill was extradited from Portugal later in the year following standard international-arrest-warrant procedures. Both entered not-guilty pleas at arraignment. Defense filings argued that publishing open-source privacy software and operating a non-custodial CoinJoin coordinator did not constitute operating a money transmitting business under the federal statute, drawing on earlier guidance from FinCEN regarding non-custodial services.

The prosecution's theory was that Samourai exercised sufficient control over the Whirlpool mixing process to qualify as a money transmitter under 18 USC 1960, regardless of whether user funds ever touched Samourai-controlled addresses.

## Late 2024: plea agreements

Both defendants ultimately accepted plea agreements rather than proceed to trial. The agreed-to charges focused on the money-transmission statute rather than the underlying money-laundering conspiracy. The plea deals were entered in late 2024 with sentencing scheduled for 2025.

## 2025: sentencing

In 2025, Rodriguez was sentenced to five years and Hill to four. The [sentencing update](https://samourai-wallet.io/samourai-wallet-sentencing-update) covers the specific structure: the sentences combined time for the plea-accepted charges, forfeiture of Samourai-related fees collected during operations, and a period of post-release supervision. Importantly, neither sentence included a forfeiture order against end users. The forfeiture applied to operator revenue.

That distinction matters. It means ordinary Samourai Wallet users whose coins happened to pass through Whirlpool are not the targets of any active forfeiture order arising from this case. Your BTC remains yours, controlled by your seed phrase. Recovery is covered in the [30-minute recovery guide](https://samourai-wallet.io/recover-samourai-wallet-funds).

## What the case changed

Operationally:

- The Samourai Wallet mobile app no longer functions. The backend is gone permanently.
- Whirlpool CoinJoin coordination via Samourai's infrastructure stopped in April 2024.
- The official samouraiwallet.com domain is under DOJ control.

Technically:

- Nothing about Bitcoin's protocol. Bitcoin continued working unchanged.
- Nothing about user-held keys. Your seed phrase still derives your UTXOs exactly as it did before.

Legally:

- Open-source CoinJoin coordinators are now high-risk projects for US-based developers. Wasabi restructured its operator entity partly in response. Newer coordinators tend to launch from jurisdictions with clearer guidance.
- The case is cited in ongoing debates over FinCEN's non-custodial software guidance.

## What it meant for the Free Samourai Movement

The [Free Samourai Movement](https://samourai-wallet.io/free-samourai-wallet-movement) formed in 2024 as a volunteer advocacy project supporting Rodriguez and Hill, maintaining recovery documentation, and arguing publicly that writing privacy software is protected activity. The [SAMOURAI token page](https://samourai-wallet.io/samourai-token-privacy-coin) archives the community-issued token associated with that advocacy. Both efforts continue into 2026 - this repository is part of the same broader effort.

## What users should do in 2026

Three things.

1. Recover your BTC using a modern desktop wallet. The [30-minute recovery guide](https://samourai-wallet.io/recover-samourai-wallet-funds) walks through Sparrow and Electrum step by step.
2. Pick a path forward. [Best Samourai Wallet alternatives](https://samourai-wallet.io/best-samourai-wallet-alternatives) compares the main options.
3. Stay off sketchy mirrors and do not fall for fake recovery services. The [recovery FAQ](https://samourai-wallet.io/samourai-wallet-recovery-faq) covers the common scams.

The case is settled. The software is gone. The Bitcoin is still yours.

## Related articles

- [Samourai Wallet 2026 Status](samourai-wallet-2026-status.md)
- [Free Samourai Movement - Privacy Is Not a Crime](free-samourai-movement-privacy-not-crime.md)
- [Recover Samourai Wallet BTC in 30 Minutes](recover-samourai-wallet-btc-30-minutes.md)
- [No-KYC Bitcoin Wallets in 2026](no-kyc-bitcoin-wallets-2026.md)
