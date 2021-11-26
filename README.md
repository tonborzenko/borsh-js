# Borsh JS ESM

**Borsh ESM** is an implementation of the [Borsh] compatible with ES modules.

That package implemented as experiment, and tested only in browser.

## Examples
### Serializing an object
```javascript
const value = new Test({ x: 255, y: 20, z: '123', q: [1, 2, 3] });
const schema = new Map([[Test, { kind: 'struct', fields: [['x', 'u8'], ['y', 'u64'], ['z', 'string'], ['q', [3]]] }]]);
const buffer = borsh.serialize(schema, value);
```

### Deserializing an object
```javascript
const newValue = borsh.deserialize(schema, Test, buffer);
```

## Type Mappings

| Borsh                 | TypeScript     |
|-----------------------|----------------|
| `u8` integer          | `number`       |
| `u16` integer         | `number`       |
| `u32` integer         | `number`       |
| `u64` integer         | `BN`           |
| `u128` integer        | `BN`           |
| `u256` integer        | `BN`           |
| `u512` integer        | `BN`           |
| `f32` float           | N/A            |
| `f64` float           | N/A            |
| fixed-size byte array | `Uint8Array`   |
| UTF-8 string          | `string`       |
| option                | `null` or type |
| map                   | N/A            |
| set                   | N/A            |
| structs               | `any`          |

## Contributing

Install dependencies:
```bash
yarn install
```

Continuously build with:
```bash
yarn dev
```

Run tests:
```bash
yarn test
```

Run linter
```bash
yarn lint
```
## Publish

Prepare `dist` version by running:
```bash
yarn build
```

When publishing to npm use [np](https://github.com/sindresorhus/np).

# License
This repository is distributed under the terms of both the MIT license and the Apache License (Version 2.0).
See [LICENSE-MIT](LICENSE-MIT.txt) and [LICENSE-APACHE](LICENSE-APACHE) for details.

[Borsh]:          https://borsh.io
