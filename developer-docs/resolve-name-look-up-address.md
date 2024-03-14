---
description: >-
  The simplest thing you can to integrate vid domains is to start with a name,
  and resolve it to an address.  Think of places where users can enter names,
  such as sending transactions, chatting, etc.
---

# 🎯 Resolve Name ( Look Up Address )

The goal here is to take a name, such as `sam.vid`, and convert it to an address, such as `0:4bc69a8c3889adee39f6f1e3b2353c86f960c9b835e93397a2015a62a4823765`

{% hint style="info" %}
&#x20;`sam.vid` ➡️ `0:4bc6...3765`&#x20;
{% endhint %}

We will make use of the `provider` instance that we got in the [Getting Started](getting-started.md) section.

## Using the lookupAddress from vid-sdk

The fastest way to resolve a vid is to use the `lookupAddress` method from the [`vid-sdk`](https://www.npmjs.com/package/vid-sdk)

{% tabs %}
{% tab title="npm" %}
```bash
npm install --save vid-sdk
```
{% endtab %}

{% tab title="yarn" %}
```bash
yarn add --dev vid-sdk
```
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="172">Props</th><th>Type</th></tr></thead><tbody><tr><td>provider</td><td>ProviderRpcClient</td></tr><tr><td>path</td><td>string (ending with .vid)</td></tr></tbody></table>

{% code overflow="wrap" fullWidth="false" %}
```typescript

import { lookupAddress } from 'vid-sdk';

//We will make use of the provider instance that we got before
// pass in the provider instance and the name of the domain ending with .vid
const targetAddress = await lookupAddress(provider,"sam.vid");
// targetAddress = 0:4bc6...3765 
// returns an empty string when target address does not exist
```
{% endcode %}

**Live on CodeSandbox :**&#x20;

{% embed url="https://codesandbox.io/p/devbox/venom-id-lookup-address-v95v7c?embed=1&file=/src/App.jsx" %}

{% hint style="info" %}
**if you don't want to install the `vid-sdk` package, you can ignore and use the direct way explained below**
{% endhint %}

## Using Contract Methods And Abi

<pre class="language-typescript"><code class="lang-typescript">import { Address, ProviderRpcClient } from "everscale-inpage-provider";
import { ROOT_CONTRACT_ADDRESS } from "./constants";
// check the Overview page on the Venom ID Developer Docs Section for Deployed Root Address
import RootAbi from "abi/Root.abi.json"; 
// https://github.com/sam-shariat/venomidapp/blob/main/abi/Root.abi.json
import DomainAbi from "abi/Domain.abi.json";
// https://github.com/sam-shariat/venomidapp/blob/main/abi/Domain.abi.json

async function lookupAddress
(provider: ProviderRpcClient,path: string) 
{
  if (!provider) return;
  
<strong>  const rootContract = new provider.Contract(
</strong>      RootAbi,
      new Address(ROOT_CONTRACT_ADDRESS)
    );
    
  const certificateAddr: { certificate: Address } = await rootContract.methods
    .resolve({ path: path, answerId: 0 } as never)
    .call({ responsible: true });

  const domainContract = new provider.Contract(
    DomainAbi,
    certificateAddr.certificate
  );
  
  try {
  
    const { target } = await domainContract.methods.resolve({ answerId: 0 } as never)
      .call({ responsible: true });
    
    if (target) {
      return String(target);
    } else {
      return "";
    }
  } catch (e) {
    return ""
  }
}

const targetAddress = await lookupAddress(provider,"sam.vid");
console.log(targetAddress);
// output : 0:4bc6...3765 
</code></pre>
