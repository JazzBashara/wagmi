<script setup>
const packageName = 'wagmi'
const actionName = 'getEnsAvatar'
const typeName = 'GetEnsAvatar'
const TData = 'string | null'
const TError = 'GetEnsAvatarError'
</script>

# useEnsAvatar

Hook for fetching ENS avatar for name.

## Import

```ts
import { useEnsAvatar } from 'wagmi'
```

## Usage

::: code-group
```tsx [index.tsx]
import { useEnsAvatar } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

::: warning
Since ENS names prohibit certain forbidden characters (e.g. underscore) and have other validation rules, you likely want to [normalize ENS names](https://docs.ens.domains/contract-api-reference/name-processing#normalising-names) with [UTS-46 normalization](https://unicode.org/reports/tr46) before passing them to `useEnsAvatar`. You can use Viem's built-in [`normalize`](https://viem.sh/docs/ens/utilities/normalize) function for this.
:::

## Parameters

```ts
import { type UseEnsAvatarParameters } from 'wagmi'
```

---

### blockNumber

`bigint | undefined`

Block number to get ENS avatar at.

::: code-group
```ts [index.ts]
import { useEnsAvatar } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    blockNumber: 17829139n, // [!code focus]
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### blockTag

`'latest' | 'earliest' | 'pending' | 'safe' | 'finalized' | undefined`

Block tag to get ENS avatar at.

::: code-group
```ts [index.ts]
import { useEnsAvatar } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    name: normalize('wagmi-dev.eth'),
    blockTag: 'latest', // [!code focus]
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

---

### chainId

`config['chains'][number]['id'] | undefined`

ID of chain to use when fetching data.

::: code-group
```tsx [index.tsx]
import { useEnsAvatar } from 'wagmi'
import { mainnet } from 'wagmi/chains' // [!code focus]
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    name: normalize('wagmi-dev.eth'),
    chainId: mainnet.id, // [!code focus]
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### gatewayUrls

`{ ipfs?: string | undefined; arweave?: string | undefined } | undefined`

Gateway urls to resolve IPFS and/or Arweave assets.

::: code-group
```ts [index.ts]
import { useEnsAvatar } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    gatewayUrls: { // [!code focus]
      ipfs: 'https://cloudflare-ipfs.com', // [!code focus]
    }, // [!code focus]
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### name

`string | undefined`

Name to get the avatar for. [`enabled`](#enabled) set to `false` if `name` is `undefined`.

::: code-group
```ts [index.ts]
import { useEnsAvatar } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    name: normalize('wagmi-dev.eth'), // [!code focus]
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### universalResolverAddress

`Avatar | undefined`

- Avatar of ENS Universal Resolver Contract.
- Defaults to current chain's Universal Resolver Contract address.

::: code-group
```ts [index.ts]
import { useEnsAvatar } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsAvatar({
    name: normalize('wagmi-dev.eth'),
    universalResolverAddress: '0x74E20Bd2A1fE0cdbe45b9A1d89cb7e0a45b36376', // [!code focus]
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

<!--@include: @shared/query-options.md-->

## Return Type

```ts
import { type UseEnsAvatarReturnType } from 'wagmi'
```

<!--@include: @shared/query-result.md-->

<!--@include: @shared/query-imports.md-->

## Action

[getEnsAvatar](/core/actions/getEnsAvatar)