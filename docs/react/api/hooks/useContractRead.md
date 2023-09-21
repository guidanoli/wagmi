<script setup>
const packageName = 'wagmi'
const actionName = 'readContract'
const typeName = 'ReadContract'
const TData = 'ReadContractReturnType'
const TError = 'ReadContractError'
</script>

# useContractRead

Calls a **read-only** function on a contract, and returns the response.

A **read-only** function (constant function) on a Solidity contract is denoted by a pure or view keyword. They can only read the state of the contract, and cannot make any changes to it. Since read-only methods do not change the state of the contract, they do not require any gas to be executed, and can be called by any user without the need to pay for gas.

## Import

```ts
import { useContractRead } from 'wagmi'
```

## Usage

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'totalSupply',
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

## Parameters

```ts
import { type UseContractReadParameters } from 'wagmi'
```

---

### abi

`Abi | undefined`

The contract's ABI. Check out the [TypeScript docs](/react/typescript#const-assert-abis-typed-data) for how to set up ABIs for maximum type inference and safety.

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi' // [!code focus]

function App() {
  const result = useContractRead({
    abi: erc20Abi, // [!code focus]
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'totalSupply',
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

### account

`Account | undefined`

Account to use when calling the contract (`msg.sender`).

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'balanceOf',
    args: ['0x6b175474e89094c44da98b954eedeac495271d0f'],
    account: '0xd2135CfB216b74109775236E36d4b433F1DF507B', // [!code focus]
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

### address

`Address | undefined`

The contract's address.

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f', // [!code focus]
    functionName: 'totalSupply',
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

### args

`readonly unknown[] | undefined`

- Arguments to pass when calling the contract.
- Inferred from [`abi`](#abi) and [`functionName`](#functionname).

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'balanceOf',
    args: ['0x6b175474e89094c44da98b954eedeac495271d0f'], // [!code focus]
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

---

### blockNumber

`bigint | undefined`

Block number to call contract at.

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'totalSupply',
    blockNumber: 17829139n, // [!code focus]
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

### blockTag

`'latest' | 'earliest' | 'pending' | 'safe' | 'finalized' | undefined`

Block tag to call contract at.

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'totalSupply',
    blockTag: 'safe', // [!code focus]
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

---

### chainId

`config['chains'][number]['id'] | undefined`

ID of chain to use when fetching data.

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { mainnet } from 'wagmi/chains' // [!code focus]
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'totalSupply',
    chainId: mainnet.id, // [!code focus]
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

### config

`Config | undefined`

[`Config`](/react/api/createConfig#config) to use instead of retrieving from the from nearest [`WagmiProvider`](/react/WagmiProvider).

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'
import { config } from './config' // [!code focus]

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'totalSupply',
    config, // [!code focus]
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

### functionName

`string | undefined`

- Function to call on the contract.
- Inferred from [`abi`](#abi).

::: code-group
```tsx [index.tsx]
import { useContractRead } from 'wagmi'
import { erc20Abi } from './abi'

function App() {
  const result = useContractRead({
    abi: erc20Abi,
    address: '0x6b175474e89094c44da98b954eedeac495271d0f',
    functionName: 'balanceOf', // [!code focus]
    args: ['0x6b175474e89094c44da98b954eedeac495271d0f'],
  })
}
```
<<< @/snippets/abi.ts#erc20Abi-read[abi.ts]
<<< @/snippets/react/config.ts[config.ts]
:::

<!--@include: @shared/query-options.md-->

## Return Type

```ts
import { type UseContractReadReturnType } from 'wagmi'
```

The return type's [`data`](#data) property is inferrable via the combination of [`abi`](#abi), [`functionName`](#functionname), and [`args`](#args). Check out the [TypeScript docs](/react/typescript#const-assert-abis-typed-data) for more info.

<!--@include: @shared/query-result.md-->

<!--@include: @shared/query-imports.md-->

## Action

[`readContract`](/core/api/actions/readContract)