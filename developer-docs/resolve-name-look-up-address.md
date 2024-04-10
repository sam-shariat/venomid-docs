---
description: >-
  The simplest thing you can do to integrate venom domains is to resolve a name
  to an address.  Think of places where users can enter names, such as sending
  transactions, chatting, etc.
---

# 🎯 Resolve Name ( Look Up Address )

The goal here is to take a name, such as `sam.venom`, and convert it to an address, such as `0:4bc69a8c3889adee39f6f1e3b2353c86f960c9b835e93397a2015a62a4823765`

{% hint style="info" %}
&#x20;`sam.venom`➡️ `0:4bc6...3765`&#x20;
{% endhint %}

We will make use of the `provider` instance that we got in the [Getting Started](getting-started.md) section.

## Using Contract Methods And Abi

<pre class="language-typescript"><code class="lang-typescript">import { Address, ProviderRpcClient } from "everscale-inpage-provider";
const { VENOMID_ROOT_CONTRACT_ADDRESS } from "./constants";
// mainnet : 

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

const targetAddress = await lookupAddress(provider,"sam.venom");
console.log(targetAddress);
// output : 0:4bc6...3765 
</code></pre>
