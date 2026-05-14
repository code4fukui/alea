# Alea

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A simple copy-and-paste implementation of Johannes Baagøe's Alea PRNG.

## Features
- Provides a more modern and performant pseudo-random number generator (PRNG) than the built-in `Math.random()` in JavaScript.
- Allows synchronizing the state of two Alea PRNGs via the `importState` and `exportState` methods.

## Installation
```bash
npm install alea
```
Or
```js
import Alea from 'https://code4fukui.github.io/alea/alea.js'
```

## Usage
```js
import Alea from 'alea'

const prng = new Alea() // add an optional seed param

const nextRandnum = prng() // just call the return value of Alea
```

## Synchronization
```js
const prng1 = new Alea(200)

prng1()
prng1()

// after generating a few random numbers, we will initialize a new PRNG

const prng2 = Alea.importState(prng1.exportState())

// this should echo true, true, true
console.log(prng2() == prng1())
console.log(prng2() == prng1())
console.log(prng2() == prng1())
```

The synchronization feature allows clients to join a simulation (e.g., a game) running on a server and have their local simulation fully in sync with the server, without depending entirely on the server for every update.

## License
MIT License — see [LICENSE](LICENSE).