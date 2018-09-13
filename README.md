# Generic Chain

Create Middleware by chaining functions. Based on [benawad/graphql-chain](https://github.com/benawad/graphql-chain)

## Install

```
yarn add generic-chain
```

## How to use

### Step 1

Create middlewares

```js
const validate: MiddlewareResolver = (
  next,
  ctx
) => {
  if (ctx.name.length > 10) {
    throw new Error("too long");
  }

  return next();
};
```

### Step 2

Chain Middleware

```
import { chain } from "generic-chain";

// chain all your middlewares
const testMiddleware = chain([
  validate,
  cache,
]);
```

### Step 3

Run the Chain

```
const somethingHappened = () => testMiddleware();
```


The execution sequence will be `getUserMiddleware` -> `authorizationMiddleware` -> `validationMiddleware` -> `hello`

Checkout the `examples` directory for complete examples
