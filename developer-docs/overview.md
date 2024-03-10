---
description: >-
  Venom ID Domains (VID) is a distributed, open, and extensible naming system
  based on The Open Network Virtual Machine (TVM)-compatible blockchains,
  currently operating on the venom testnet blockchain.
---

# ➡️ Overview

VID's primary function is to map human-readable names like 'sam.vid' to machine-readable identifiers, including wallet addresses, IP or ADNL addresses, traditional domain names, and other DNS protocol records. Venom ID also supports reverse resolution, enabling the association of metadata, such as canonical names or interface descriptions, with wallet addresses.

VID domains are implemented as Non-Fungible Tokens (NFTs) using the [TIP-4 token standard](https://docs.venom.foundation/standards/TIP/TIP-4/core-description/), which allows the owner to manage records and create subdomains as child NFTs.

VID operates on a system of dot-separated hierarchical names called domains, with the owner of a domain having full control over subdomains. Top-level domains, like '.vid' and '.test', are managed by the Root smart contract, which deploys new domain and subdomain certificates and ensures seamless integration between various components and interfaces.

### Deployed Roots[​](https://ever-name-docs.netlify.app/#deployed-domains) <a href="#deployed-domains" id="deployed-domains"></a>

VID is currently deployed on the **Venom Testnet Blockchain**

<table><thead><tr><th width="97">TLD</th><th>Contract Address</th></tr></thead><tbody><tr><td>vid</td><td><a href="https://testnet.venomscan.com/accounts/0:5475e9e7b9d178f4c35cd1136e83a100ca95e28b38c5c52d0689771372ba43ec">0:5475e9e7b9d178f4c35cd1136e83a100ca95e28b38c5c52d0689771372ba43ec</a></td></tr></tbody></table>

{% hint style="info" %}
You can try VID out for yourself now by using the [Venom ID Platform](https://venomid.network)
{% endhint %}

{% content-ref url="getting-started.md" %}
[getting-started.md](getting-started.md)
{% endcontent-ref %}

If you want to jump right in, check out our code Examples
