# 🔄 List Names

using the example below, you can retrieve all the names a venom account address owns.

{% hint style="info" %}
`0:4bc6...3765` ➡️ `sam.vid, samydo.vid, samshariat.vid`
{% endhint %}

```typescript
async function lookupNames(
  provider: ProviderRpcClient,
  address: string,
  limit?: number
): Promise<string[]> {

  if (!provider) return [];

  const rootContract = new provider.Contract(rootAbi, new Address(ROOT_CONTRACT_ADDRESS));

  const { codeHash : _codeHash } = await rootContract.methods
  .expectedCertificateCodeHash({ target: new Address(address) , sid:1 , answerId:0 } as never)
  .call();
  if (!_codeHash) {
    return [];
  }

  const codeHash = BigInt(_codeHash).toString(16).padStart(64, '0')

  const addresses = await provider?.getAccountsByCodeHash({ codeHash, limit });
  console.log(addresses);
  if (!addresses.accounts || addresses.accounts.length === 0) {
    return [];
  }

  const nfts = await Promise.all(addresses.accounts.map(async (indexAddress) => {
    try {
      console.log(indexAddress)
      const nftContract = new provider.Contract(nftAbi, indexAddress);
      const getJsonAnswer = (await nftContract.methods.getJson({ answerId: 0 } as never).call()) as { json: string };
      const _nftJson = JSON.parse(getJsonAnswer.json ?? "{}") as BaseNftJson;
      if (address === _nftJson.target) {
        return String(_nftJson.name);
      } else {
        return '';
      }
    } catch (e) {
      return '';
    }
  }));

  return nfts.filter((nft) => nft !== null && nft !== undefined && nft.length > 3);
}

```
