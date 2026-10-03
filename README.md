# Coin Machine for Home Assistant

The Home Assistant add-on listing for Coin Machine, an AI deal analyst for coin flippers, collectors and dealers.

The add-on's image is private, so Home Assistant needs a read-only GitHub token to download it. Once:

1. [Create a GitHub token](https://github.com/settings/tokens/new?scopes=read:packages&description=Home%20Assistant%20Coin%20Machine) (only **read:packages** is ticked) and copy it.
2. [Open the add-on store](https://my.home-assistant.io/redirect/supervisor_store/), then the menu (three dots, top right) > **Registries**, and add server `ghcr.io`,
   your GitHub user name, and the token as the password.
3. [Add this repository to Home Assistant](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Fdsdadsasdaaaaaaaa%2Fcoin-machine-ha).
4. [Open the Coin Machine add-on](https://my.home-assistant.io/redirect/supervisor_addon/?addon=53ba94f3_coin_machine&repository_url=https%3A%2F%2Fgithub.com%2Fdsdadsasdaaaaaaaa%2Fcoin-machine-ha) and choose **Install**.

The add-on's Documentation tab has the rest.
