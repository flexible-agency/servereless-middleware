# Serverless Middleware

Some helpers for writing API endpoints using AWS Lambda and [Laconia](https://github.com/laconiajs/laconia).

---

## Installation

```shell
yarn add @flexible-agency/serverless-middleware
```

## Example usage

```js
import { middleware, auth } from '@flexible-agency/serverless-middleware';

const dependencies = () => ({
	// dependencies for the Laconia dependency injector
});

export const app = async({ query, path, body }, { currentUser, /* dependences */ }) => {
	// if `auth` is included in the second param of `middleware`, currentUser
	// will be an object in the form of `{ id, groups, email, ... }`

	// your business logic goes here

	return {
		success: true,
		text: 'Hello, world!'
	};
}

export const handler = middleware(app, [auth]).register(dependencies);
```