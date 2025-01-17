# paillier-lib

This package provides a simple implementation of the Paillier cryptosystem using gmpy2.

# Usage

```
from paillierlib import paillier
from gmpy2 import mpz

key_pair = paillier.keygen()  # Optional param.: bit size (default = 2048)

m1 = mpz(10)
m2 = mpz(1)
c1 = paillier.encrypt(m1, key_pair.public_key)
c2 = paillier.encrypt(m2, key_pair.public_key)

# Example homomorphic operations
# Addition
paillier.decrypt(c1 + c2, key_pair.private_key) # => 11
paillier.decrypt(c1 - c2, key_pair.private_key) # => 9
paillier.decrypt(c1 + c1 + c2, key_pair.private_key) # => 21

# Multiplication (ciphertext with plaintext)
m3 = mpz(2)
paillier.decrypt(c1 * m3, key_pair.private_key) # => 20

```

# Tests
Located in ./paillierlib/test_paillier.py. Execute using pytest:
```
pytest
```

# Requirements

gmpy2 (tested v2.0.8)

# Planned Work
* Encode inputs, rather than requiring GMP MPZ objects.
