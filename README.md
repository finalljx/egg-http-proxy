# egg-http-proxy

[![NPM version][npm-image]][npm-url]
[![build status][travis-image]][travis-url]
[![Test coverage][codecov-image]][codecov-url]
[![David deps][david-image]][david-url]
[![Known Vulnerabilities][snyk-image]][snyk-url]
[![npm download][download-image]][download-url]

[npm-image]: https://img.shields.io/npm/v/egg-http-proxy.svg?style=flat-square
[npm-url]: https://npmjs.org/package/egg-http-proxy
[travis-image]: https://img.shields.io/travis/chunkai1312/egg-http-proxy.svg?style=flat-square
[travis-url]: https://travis-ci.org/chunkai1312/egg-http-proxy
[codecov-image]: https://img.shields.io/codecov/c/github/chunkai1312/egg-http-proxy.svg?style=flat-square
[codecov-url]: https://codecov.io/github/chunkai1312/egg-http-proxy?branch=master
[david-image]: https://img.shields.io/david/chunkai1312/egg-http-proxy.svg?style=flat-square
[david-url]: https://david-dm.org/chunkai1312/egg-http-proxy
[snyk-image]: https://snyk.io/test/npm/egg-http-proxy/badge.svg?style=flat-square
[snyk-url]: https://snyk.io/test/npm/egg-http-proxy
[download-image]: https://img.shields.io/npm/dm/egg-http-proxy.svg?style=flat-square
[download-url]: https://npmjs.org/package/egg-http-proxy

Configure proxy middleware for egg. Use [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware).

## Install

```bash
$ npm i egg-http-proxy --save
```

## Usage

```js
// {app_root}/config/plugin.js
exports.httpProxy = {
  enable: true,
  package: 'egg-http-proxy',
};
```

## Configuration

Proxy `/api` requests to `http://www.example.org`:

```js
// {app_root}/config/config.default.js
exports.httpProxy = {
  '/api': 'http://www.example.org'
};
```

A request to `/api/users` will now proxy the request to `http://www.example.org/api/users`.

If you don't want `/api` to be passed along, we need to rewrite the path:

```js
// {app_root}/config/config.default.js
exports.httpProxy = {
  '/api': {
    target: 'http://www.example.org',
    pathRewrite: {'^/api' : ''}
  }
};
```

For more advanced usages, checkout [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware#options) options documentation.

## Questions & Suggestions

Please open an issue [here](https://github.com/chunkai1312/egg-http-proxy/issues).

## License

[MIT](LICENSE)
