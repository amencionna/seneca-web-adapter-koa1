# Seneca Web Adapter Koa

[![Build Status][travis-badge]][travis-url]
[![Coverage Status][coveralls-badge]][coveralls-url]

This is an adapter for [seneca-web](https://github.com/senecajs/seneca-web/) using koa/koa-routes.

## Installation

Peer dependencies have been specified for `koa`, `koa-router` and `seneca-web`
They need to be present for this to work at all.

```
npm install --save koa 
npm install --save koa-router
npm install --save seneca
npm install --save seneca-web
npm install --save seneca-web-adapter-koa1
```

## Usage

Please refer to the seneca-web documentation on how to load routes.

You can require this module as the adapter when using the SenecaWeb plugin

```js
const Seneca = require('seneca')
const SenecaWeb = require('seneca-web')
const Koa = require('koa')
const Router = require('koa-router')
const app = Koa()
const seneca = Seneca()
seneca.use(SenecaWeb, {
  context: Router(),
  adapter: require('seneca-web-adapter-koa1')
})
seneca.ready(() => {
  app.use(seneca.export('web/context')().routes())
})
```

## Note

Most of the seneca-web documents refer to passing the application as the `context` parameter.
Doing this with koa will result in unexpected explosions. Koa Router must be used. 

[travis-badge]: https://travis-ci.org/senecajs/seneca-web-adapter-koa1.svg?branch=master
[travis-url]: https://travis-ci.org/senecajs/seneca-web-adapter-koa1
[coveralls-badge]: https://coveralls.io/repos/github/senecajs/seneca-web-adapter-koa1/badge.svg?branch=master
[coveralls-url]: https://coveralls.io/github/senecajs/seneca-web-adapter-koa1?branch=master
