# Crypto Web Utils

## Installation

```bash
npm install @shardus/crypto-web
# OR yarn add @shardus/crypto-web
```

## Usage

```ts
const crypto = require('@shardus/crypto-web')

/*
  Module has an asynchronous initialize function that takes in a 32-byte hex key as required by node-sodium for generic hashing.
  Initialize function must be awaited before utilizing any other functions in your code.
*/
await crypto.initialize('64f152869ca2d473e4ba64ab53f49ccdb2edae22da192c126850970e788af347')

// Uses json-stable-stringify to stringify an object in a consistent sorted manner; returns a string
crypto.stringify(obj)

/*
  Returns a 32-byte random hex string by default, otherwise you can
  specify how many bytes you would like to generate
*/
crypto.randomBytes([bytes])

// Returns the hash of the input, output format can be specified as 'hex' or 'buffer'
crypto.hash(input [, fmt])

/*
  Returns the hash of the provided object as a hex string, optional
  parameter to hash the object without the "sign" field (default is
  false, can be passed true to hash without "sign")
*/
crypto.hashObj(obj [, removeSign])

// Generates and returns {publicKey, secretKey} as hex strings
crypto.generateKeypair()

// Returns a signature obtained by signing the input with the sk
crypto.sign(input, sk)

/*
  Attaches a sign field to the input object, containing a signed version
  of the hash of the object, along with the public key of the signer
*/
crypto.signObj(obj, sk, pk)

// Returns true if the input was signed by the owner of the pk
crypto.verify(input, sig, pk)

/*
  Returns true if the hash of the object minus the sign field matches
  the signed message in the sign field
*/
crypto.verifyObj(obj)

```
