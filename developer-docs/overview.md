---
description: >-
  Venom ID Domains (.venom) is a distributed, open, and extensible naming system
  based on The Open Network Virtual Machine (TVM)-compatible blockchains.
---

# ➡️ Overview

Venom ID's primary function is to map human-readable names like 'sam.venom' to machine-readable identifiers, including wallet addresses, IP or ADNL addresses, traditional domain names, and other DNS protocol records. Venom ID also supports reverse resolution , enabling the association of metadata, such as canonical names or interface descriptions, with wallet addresses.

{% hint style="info" %}
reverse resolution currently is in the form of listing names, primary names are coming soon
{% endhint %}

.venom domains are implemented as Non-Fungible Tokens (NFTs) using the [TIP-4 token standard](https://docs.venom.foundation/standards/TIP/TIP-4/core-description/), which allows the owner to manage records and create subdomains as child NFTs.

Venom ID operates on a system of dot-separated hierarchical names called domains, with the owner of a domain having full control over subdomains. Top-level domains, like '.venom' and '.test', are managed by the Root smart contract, which deploys new domain and subdomain certificates and ensures seamless integration between various components and interfaces.

### Deployed Roots[​](https://ever-name-docs.netlify.app/#deployed-domains) <a href="#deployed-domains" id="deployed-domains"></a>

<table><thead><tr><th width="116">TLD</th><th width="100">Network</th><th>Contract Address</th></tr></thead><tbody><tr><td>venom</td><td>Venom Mainnet</td><td><a href="https://venomscan.com/accounts/0:2b353a0c36c4c86a48b0392c69017a109c8941066ed1747708fc63b1ac79e408">0:2b353a0c36c4c86a48b0392c69017a109c8941066ed1747708fc63b1ac79e408</a></td></tr><tr><td>vid</td><td>Venom Testnet</td><td><a href="https://testnet.venomscan.com/accounts/0:5475e9e7b9d178f4c35cd1136e83a100ca95e28b38c5c52d0689771372ba43ec">0:5475e9e7b9d178f4c35cd1136e83a100ca95e28b38c5c52d0689771372ba43ec</a></td></tr></tbody></table>

{% hint style="info" %}
You can try out for yourself now by using the [Venom ID Platform](https://venomid.network)
{% endhint %}

{% content-ref url="getting-started.md" %}
[getting-started.md](getting-started.md)
{% endcontent-ref %}

If you want to jump right in, check out our code Examples
