---
description: >-
  Using The Venom ID Rest API you are able to fetch domains information through
  GET requests.
---

# 🌐 REST API

## **Looking Up a Name**

To look up a name in .venom domains, use the following URL:

```
https://www.venomid.network/api/lookup?name=[name]
```

Replace `[name]` with the name you want to look up. For example, to look up the name `sam.venom`, use the following URL:

```url
https://www.venomid.network/api/lookup?name=sam.venom
```

The response will be a string containing the target venom address of the requested name.

## **Looking Up an Address**

To look up an address in .venom domains, use the following URL:

```
https://www.venomid.network/api/lookup?address=[address]
```

Replace `[address]` with the address you want to look up. For example, to look up the address `0:4bc69a8c3889adee39f6f1e3b2353c86f960c9b835e93397a2015a62a4823765`, use the following URL:

```
https://www.venomid.network/api/lookup?address=0:4bc69a8c3889adee39f6f1e3b2353c86f960c9b835e93397a2015a62a4823765
```

The response will be a string containing the name of the requested address.&#x20;

\
