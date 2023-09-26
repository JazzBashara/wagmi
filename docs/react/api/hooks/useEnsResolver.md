<script setup>
const packageName = 'wagmi'
const actionName = 'getEnsResolver'
const typeName = 'GetEnsResolver'
const TData = 'string | null'
const TError = 'GetEnsResolverError'
</script>

# useEnsResolver

Hook for fetching ENS resolver for name.

## Import

```ts
import { useEnsResolver } from 'wagmi'
```

## Usage

::: code-group
```tsx [index.tsx]
import { useEnsResolver } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsResolver({
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

::: warning
Since ENS names prohibit certain forbidden characters (e.g. underscore) and have other validation rules, you likely want to [normalize ENS names](https://docs.ens.domains/contract-api-reference/name-processing#normalising-names) with [UTS-46 normalization](https://unicode.org/reports/tr46) before passing them to `useEnsResolver`. You can use Viem's built-in [`normalize`](https://viem.sh/docs/ens/utilities/normalize) function for this.
:::

## Parameters

```ts
import { type UseEnsResolverParameters } from 'wagmi'
```

---

### blockNumber

`bigint | undefined`

Block number to get ENS resolver at.

::: code-group
```ts [index.ts]
import { useEnsResolver } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsResolver({
    blockNumber: 17829139n, // [!code focus]
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### blockTag

`'latest' | 'earliest' | 'pending' | 'safe' | 'finalized' | undefined`

Block tag to get ENS resolver at.

::: code-group
```ts [index.ts]
import { useEnsResolver } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsResolver({
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
import { useEnsResolver } from 'wagmi'
import { mainnet } from 'wagmi/chains' // [!code focus]
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsResolver({
    chainId: mainnet.id, // [!code focus]
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### config

`Config | undefined`

[`Config`](/react/api/createConfig#config) to use instead of retrieving from the from nearest [`WagmiProvider`](/react/WagmiProvider).

::: code-group
```tsx [index.tsx]
import { useEnsResolver } from 'wagmi'
import { normalize } from 'viem/ens'
import { config } from './config' // [!code focus]

function App() {
  const result = useEnsResolver({
    config, // [!code focus]
    name: normalize('wagmi-dev.eth'),
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### name

`string | undefined`

Name to get the resolver for. [`enabled`](#enabled) set to `false` if `name` is `undefined`.

::: code-group
```ts [index.ts]
import { useEnsResolver } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsResolver({
    name: normalize('wagmi-dev.eth'), // [!code focus]
  })
}
```
<<< @/snippets/react/config.ts[config.ts]
:::

### universalResolverAddress

`Resolver | undefined`

- Resolver of ENS Universal Resolver Contract.
- Defaults to current chain's Universal Resolver Contract address.

::: code-group
```ts [index.ts]
import { useEnsResolver } from 'wagmi'
import { normalize } from 'viem/ens'

function App() {
  const result = useEnsResolver({
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
import { type UseEnsResolverReturnType } from 'wagmi'
```

<!--@include: @shared/query-result.md-->

<!--@include: @shared/query-imports.md-->

## Action

[`getEnsResolver`](/core/api/actions/getEnsResolver)