## Hot Automerge

This tests a fork of [https://github.com/automerge/automerge?files=1](Automerge) without the use of `Object.freeze`. This fork is located under `node_modules/hot-automerge`. Run with `yarn start` or `npm run start`.

A very rudimentary test on the performance impact of `Object.freeze` is available on JSPerf [https://jsperf.com/freeze-vs-seal-vs-normal/27](here). JSPerf gave a roughly 42-47% slowdown using a single `Object.freeze` call.

After removing calls to `Object.freeze` from `automerge` (`hot-automerge`), testing 0,000 inserts on my 2012 Retina MacBook Pro (2.3 GHz i7, 8GB RAM) I get:

```
automerge profile 10000 inserts: 55546.893ms
hot-automerge profile 10000 inserts: 4051.241ms
```

which gives 55s using `Object.freeze` vs. 4s without it—a ~90% performance improvement. Repeated runs gave similar results, as did changing the order of the tests.