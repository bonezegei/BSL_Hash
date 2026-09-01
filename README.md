# BSL_Hash

**BSL_Hash** is a checksum and hashing library designed for the **Bonezegei Scripting Language (BSL)**. It provides fast non-cryptographic checksums, modern hash functions, and cryptographic digests in `.bzg` scripts.

## Table of Contents
- [Installation](#installation)
- [Getting Started](#getting-started)
- [Code Examples](#code-examples)
  - [1. Checksums & Non-Cryptographic Hashes](#1-checksums--non-cryptographic-hashes)
  - [2. Cryptographic Digest Hashes](#2-cryptographic-digest-hashes)
  - [3. Complete Verification Script](#3-complete-verification-script)
- [API Reference](#api-reference)
- [License & Author](#license--author)
- [Citation](#citation)

## Installation

Install `BSL_Hash` using the BSL Package Manager (`bzg`):

```bash
bzg install hash
```

## Getting Started

To use the library in your script, include the hash module after installation and instantiate the `hash` object:

```javascript
include("lib/hash.bzg");

var h = hash();
var digest = h.sha256("Hello, Bonezegei!");
print("SHA256: " + digest);
```

## Code Examples

### 1. Checksums & Non-Cryptographic Hashes

Example calculating checksums and non-cryptographic hashes for high-speed data processing and hash table operations:

```javascript
/*
    Non-Cryptographic Hashes Example
    Author: Jofel Batutay (Bonezegei)
    Date: Sept 1, 2026
*/

include("lib/hash.bzg");

var h = hash();
var input = "Hello, Bonezegei!";

print("CRC32:       " + h.crc32(input));
print("Adler-32:    " + h.adler32(input));
print("FNV-1a:      " + h.fnv1a(input));
print("MurmurHash3: " + h.murmur3(input, 42)); // Input and Seed
print("xxHash:      " + h.xxhash(input, 0));  // Input and Seed
```

---

### 2. Cryptographic Digest Hashes

Example generating secure cryptographic hexadecimal digests from string inputs:

```javascript
/*
    Cryptographic Digest Hashes Example
    Author: Jofel Batutay (Bonezegei)
    Date: Sept 1, 2026
*/

include("lib/hash.bzg");

var h = hash();
var input = "Hello, Bonezegei!";

print("MD5:    " + h.md5(input));
print("SHA1:   " + h.sha1(input));
print("SHA256: " + h.sha256(input));
print("SHA-3:  " + h.sha3(input));
print("SHA512: " + h.sha512(input));
```

---

### 3. Complete Verification Script

A full test suite script demonstrating output verification across all supported hashing algorithms:

```javascript
/*
    BSL_Hash Test Suite
    Author: Jofel Batutay (Bonezegei)
    Date: Sept 1, 2026
*/

include("lib/hash.bzg");

function check(label, actual, expected) {
    if (actual === expected) {
        print("PASS: "  + label + "  OUTPUT: " + actual);
    } else {
        print("FAIL: " + label + "  OUTPUT: " + actual);
    }
}

var h = hash();

var input = "Hello, Bonezegei!";
var key = "super_secret_key";

print("--- Checksums & Non-Cryptographic Hashes ---");
check("CRC32:       " , h.crc32(input), "ccccf7f8");
check("Adler-32:    " , h.adler32(input), "35b905fa");
check("FNV-1a:      " , h.fnv1a(input), "59673d46");
check("MurmurHash3: " , h.murmur3(input, 42), "e95a8d40"); 
check("xxHash:      " , h.xxhash(input, 0), "59eafb70");  

print("\n--- Cryptographic Digest Hashes (Hex) ---");
check("MD5:         " , h.md5(input), "1390f98482b7ebe2668fa8f64a55b71f");
check("SHA1:        " , h.sha1(input), "bd46120f02cbe618411cbd70c0cfd37715014347");
check("SHA256:      " , h.sha256(input), "67ea37441cb5523681dd7ae769d877ddf2d510af48a052d53dcb736c3b1e5387");
check("SHA-3:       " , h.sha3(input), "206a1b8a0d0d8023622551786f1c4f1f5b99b92dcd6412212892d949749294ea");
check("SHA512:      " , h.sha512(input), "1c7e571d5f7eaf56af22af63b25d1812640d1a3ea6f758a0fe70d41a485b28a14bfbb1aa0deb671937faeeb3398c6b91853a5f3d67680686a4d018b50ec2db6d");
```

## API Reference

| Function Signature | Return Value | Description |
| :--- | :--- | :--- |
| `h.crc32(input)` | `string` (Hex) | Computes a 32-bit Cyclic Redundancy Check checksum. |
| `h.adler32(input)` | `string` (Hex) | Computes an Adler-32 checksum. |
| `h.fnv1a(input)` | `string` (Hex) | Computes a 32-bit Fowler–Noll–Vo 1a non-cryptographic hash. |
| `h.murmur3(input, seed)` | `string` (Hex) | Computes a 32-bit MurmurHash3 non-cryptographic hash with a custom seed. |
| `h.xxhash(input, seed)` | `string` (Hex) | Computes an xxHash non-cryptographic hash with a custom seed. |
| `h.md5(input)` | `string` (Hex) | Computes a 128-bit MD5 cryptographic hash digest. |
| `h.sha1(input)` | `string` (Hex) | Computes a 160-bit SHA-1 cryptographic hash digest. |
| `h.sha256(input)` | `string` (Hex) | Computes a 256-bit SHA-256 cryptographic hash digest. |
| `h.sha3(input)` | `string` (Hex) | Computes a SHA-3 cryptographic hash digest. |
| `h.sha512(input)` | `string` (Hex) | Computes a 512-bit SHA-512 cryptographic hash digest. |

---

## License & Author

* **Author:** Jofel Batutay ([Bonezegei](https://github.com/bonezegei))
* **Website:** [bonezegei.com](https://bonezegei.com)

## Citation 
[![DOI](https://zenodo.org/badge/1352961206.svg)](https://doi.org/10.5281/zenodo.22217630)

If you use this library, please cite it as below:

**APA Format:**

Batutay, J. (2026). *bonezegei/BSL_Hash* [Computer software]. https://doi.org/10.5281/zenodo.22217630
