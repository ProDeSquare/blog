---
title: "Create Monero (XMR) Wallet"
excerpt: Monero is a private, decentralized cryptocurrency. Create a wallet now to send and receive funds.
date: 2022-07-29T23:12:15+05:00
draft: false
hero: /images/posts/create-monero-wallet/hero.webp
authors:
    - Hamza Mughal
---

## What is Monero (XMR)?

The official **Monero (XMR)** [documentation](https://getmonero.org) states:
> Monero is a private, decentralized cryptocurrency that keeps your finances confidential and secure.

This means **Monero (XMR)** is untrackable unlike **Bitcoin (BTC)**.

## Download & Install

You can easily find installers for the following systems on the [downloads page](https://getmonero.org/downloads)
- GNU/Linux
- Windows
- MacOS

While on linux you can install it with the default package manager of your respective distribution.

```shell
# Arch based distributions
$ sudo pacman -S monero monero-gui
```

## Creating the wallet

You can click the icon to launch the **Monero GUI Wallet** or alternatively on **GNU/Linux** you can run the following:
```shell
# For the GUI version (used in this article)
$ monero-wallet-gui

# For the CLI version (if installed)
$ monero-wallet-cli
```

This would open up the preffered version of the wallet. The GUI would look like this.

![Monero GUI wallet type selection page](/images/posts/create-monero-wallet/monero-landing-page.webp)

Choose **Simple Mode** and if it asks for confirmation, confirm it.

![Monero GUI wallet welcome page](/images/posts/create-monero-wallet/monero-welcome-page.webp)

Click **Create a new wallet** and it would ask you for the details.

![Create a new wallet page](/images/posts/create-monero-wallet/create-a-new-wallet.webp)

Fill in the following information and click next:
- Wallet name 
- Wallet location (can be any location on your computer)

In most cases **Monero GUI Wallet** would fill in the information automatically for you.

### Caution

Save the **Mnemonic seed** generated and **never** share it with anyone, this would be required to recover your wallet.

### Creating a password

After clicking next it would ask you to generate the local password for your wallet. It could contain letters, numbers and symbols. While creating a **password** make sure to **remember** it because it cannot be recovered.

![Create a password](/images/posts/create-monero-wallet/generate-password.webp)

Click next to confirm the password and it would show you your wallet details, click next and it will ask you for the password you just created. Enter the password and it would take you to your newly created **XMR** wallet. You get a **primary address** where you can receive payments and you can create a new one anytime.

## Create a new address

To create a new address switch to the **receive** tab from the left sidepanel and click create new address. It would prompt you for a label, that would help you keep track of which address got the payment. For example you can create seperate addresses for your blog and github profile, so you would know where the payment came from. Copy the address and paste or send it to receive payment from someone.

## Recovering a wallet

![Monero GUI wallet type selection page](/images/posts/create-monero-wallet/monero-welcome-page.webp)

Click **Recover wallet from keys or mnemonic seed** and fill in the following:
- Wallet name
- Wallet location
- 25 word mnemonic seed
- Restore height (This would make the recovery process fast)

And click next, create a password and you are all set.