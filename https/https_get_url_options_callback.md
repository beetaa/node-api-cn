<!-- YAML
added: v0.3.6
changes:
  - version: v10.9.0
    pr-url: https://github.com/nodejs/node/pull/21616
    description: The `url` parameter can now be passed along with a separate
                 `options` object.
  - version: v7.5.0
    pr-url: https://github.com/nodejs/node/pull/10638
    description: The `options` parameter can be a WHATWG `URL` object.
-->
* `url` {string | URL}
* `options` {Object | string | URL} 接受与 [`https.request()`] 相同的 `options`, `method` 始终设置为 `GET`。
* `callback` {Function}

类似 [`http.get()`]，但是用于 HTTPS。

`options` 可以是对象、字符串、或 [`URL`] 对象。
如果 `options` 是一个字符串, 则自动使用 [`new URL()`] 解析它。
如果它是一个 [`URL`] 对象，则将自动转换为普通的 `options` 对象。

```js
const https = require('https');

https.get('https://encrypted.google.com/', (res) => {
  console.log('状态码:', res.statusCode);
  console.log('请求头:', res.headers);

  res.on('data', (d) => {
    process.stdout.write(d);
  });

}).on('error', (e) => {
  console.error(e);
});
```

