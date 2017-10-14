<!-- YAML
added: v0.11.2
-->

* `code` {number} 如果推出正常,那么退出代码为{number}类型.
* `signal` {string} 造成指定进程被杀.死的事件名称（如`'SIGHUP'`）.

虽然这个和`cluster.on('exit')`事件类似，但是却针对特定的进程。

```js
const worker = cluster.fork();
worker.on('exit', (code, signal) => {
  if (signal) {
    console.log(`worker was killed by signal: ${signal}`);
  } else if (code !== 0) {
    console.log(`worker exited with error code: ${code}`);
  } else {
    console.log('worker success!');
  }
});
```

