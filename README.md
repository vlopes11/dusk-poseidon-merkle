# Poseidon Merkle Tree

[![Build Status](https://travis-ci.com/dusk-network/dusk-poseidon-merkle.svg?branch=master)](https://travis-ci.com/dusk-network/dusk-poseidon-merkle)
[![Repository](https://dusk-network.github.io/dusk-poseidon-merkle/repo-badge.svg)](https://github.com/dusk-network/dusk-poseidon-merkle)
[![Documentation](https://dusk-network.github.io/dusk-poseidon-merkle/badge.svg)](https://dusk-network.github.io/dusk-poseidon-merkle/dusk_poseidon_merkle/index.html)

Reference implementation for the Poseidon Merkle function.

The `Poseidon` structure will accept a number of inputs equal to the arity of the tree.

## Build

A few environment variables will be read in the build process.

* `POSEIDON_MERKLE_ARITY`

    Represents the arity of the merkle tree. This is also the maximum number of elements the poseidon hash will accept. Defaults to `4`.


* `POSEIDON_MERKLE_WIDTH`

    Represents the merkle tree width. Defaults to `64`.

* `POSEIDON_FULL_ROUNDS`

    Represents the number of full rounds performed during the permutation. Defaults to `8`.

* `POSEIDON_PARTIAL_ROUNDS`

    Represents the number of partial rounds performed during the permutation. Defaults to `59`.

## Example

```rust
use dusk_poseidon_merkle::{MERKLE_ARITY, Poseidon, Scalar};

let mut h = Poseidon::default();
for i in 0..MERKLE_ARITY {
    h.push(Scalar::from(i as u64)).unwrap();
}

let hash = h.hash();
println!("{:x?}", hash.as_bytes());
```

## Reference

[Starkad and Poseidon: New Hash Functions for Zero Knowledge Proof Systems](https://eprint.iacr.org/2019/458.pdf)
