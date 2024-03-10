---
description: >-
  Currently , our guides provide coverage of React and Next.js. As we continue
  to expand, we will incorporate additional tools and libraries to enhance our
  documents.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 📝 Getting Started

{% hint style="info" %}
The code examples given in this document assumes that it is executed within a DApp browser environment, such as Chrome with the [Venom Wallet](https://venomwallet.com) extension installed. This environment provides access to the provider object. For additional information on how to connect to the venom blockchain please refer to [venom documentation](https://venom.guide/frontend/connect)&#x20;
{% endhint %}

## Installation

To begin, let's establish a connection between our app and the [Venom Wallet](https://venomwallet.com).&#x20;

To accomplish this, we will utilize the [Venom-Connect](https://www.npmjs.com/package/venom-connect) library. This library offers a convenient interface for creating a connect popup within our app for the Venom wallet, and also provides an interface for interacting with the Venom network.&#x20;

{% hint style="info" %}
For detailed information on how to use Venom-Connect, please refer to [Venom Docs](https://docs.venom.foundation/build/development-guides/how-to-create-your-own-fungible-tip-3-token/venom-in-action/extend-our-tokensale-with-frontend).
{% endhint %}

First, make sure to install the [`venom-connect`](https://www.npmjs.com/package/venom-connect) , [everscale-inpage-provider](https://www.npmjs.com/package/everscale-inpage-provider) and [everscale-standalone-client](https://www.npmjs.com/package/everscale-standalone-client) packages.

{% tabs %}
{% tab title="npm" %}
```bash
npm install --save venom-connect everscale-inpage-provider everscale-standalone-client
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add --dev venom-connect everscale-inpage-provider everscale-standalone-client
```
{% endtab %}
{% endtabs %}



before we can start looking up vid domain addresses, we need to establish a connection between our app and venom wallet to get access to the  `provider` object.&#x20;

{% hint style="info" %}
If you already have access to the provider object ( ProviderRpcClient ) in your environment, then you can ignore this step.
{% endhint %}

```jsx
import { VenomConnect } from "venom-connect";
import { ProviderRpcClient } from "everscale-inpage-provider";

const venomConnect = new VenomConnect({
  // venom connect config
  // check out https://codesandbox.io/p/devbox/venom-id-lookup-address-v95v7c
});

venomConnect.connect() // open pop up for venom wallet connection

const provider = await venomConnect.checkAuth(); 
// we need the provider instance for later

```

We need the `provider` instance for later to be able to send and retrieve data from the venom blockchain and venom id registry.
