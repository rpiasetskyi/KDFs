# RustCrypto: Concat KDF

[![crate][crate-image]][crate-link]
[![Docs][docs-image]][docs-link]
![Apache2/MIT licensed][license-image]
![Rust Version][rustc-image]
[![Project Chat][chat-image]][chat-link]
[![Build Status][build-image]][build-link]

Pure Rust implementation of the Concatenation Key Derivation Function (Concat KDF) generic over hash function. 
This function is described in the section 5.8.1 of [NIST SP 800-56A, Recommendation for Pair-Wise Key Establishment
Schemes Using Discrete Logarithm Cryptography](https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-56ar.pdf).

# Usage

The most common way to use Concat KDF is as follows: you generate a shared secret with other party (e.g. via Diffie-Hellman algorithm) 
and use key derivation function to derive a shared key.

```rust
let mut key = [0u8; 32];
concat_kdf::derive_key_into::<sha2::Sha256>(b"shared-secret", b"other-info", &mut key).unwrap();
```
