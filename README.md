# fastify-routes

![CI](https://github.com/fastify/fastify-routes/workflows/CI/badge.svg)
[![NPM version](https://img.shields.io/npm/v/fastify-routes.svg?style=flat)](https://www.npmjs.com/package/fastify-routes)
[![Known Vulnerabilities](https://snyk.io/test/github/fastify/fastify-routes/badge.svg)](https://snyk.io/test/github/fastify/fastify-routes)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://standardjs.com/)

This plugin decorates Fastify instance with `routes`, which is a [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map) of registered routes. Note that you have to register this plugin
before registering any routes so that it can collect all of them.

## Example

```js
const fastify = require('fastify')()

fastify.register(require('fastify-routes'))

fastify.get('/hello', {}, (request, reply) => {
  reply.send({ hello: 'world' })
})

fastify.listen(3000, (err, address) => {
  if (err) {
    console.error(err)
    return
  }
  console.log(fastify.routes)
  /* will output a Map with entries:
  {
    '/hello': {
      get: {
        method: 'GET',
        url: '/hello',
        schema: Object,
        handler: <Function>,
        prefix: <String>,
        logLevel: <String>,
        bodyLimit: <Number>
      }
    }
  }
  */
})

```

## License

MIT License
