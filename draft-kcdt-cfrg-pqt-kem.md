---
title: "Hybrid PQ/T Key Encapsulation Mechanism"
category: info

docname: draft-kcdt-cfrg-pqt-kem-latest
submissiontype: IRTF
number:
date:
consensus: true
v: 3
area: "IRTF"
workgroup: "Crypto Forum"
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: "Crypto Forum"
  type: "Research Group"
  mail: "cfrg@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/cfrg"
  github: "bwesterb/pqt-kem"
  latest: "https://bwesterb.github.io/pqt-kem/draft-kcdt-cfrg-pqt-kem.html"

author:
 -
    fullname: TBD
    organization: TBD
    email: TBD

normative:

informative:


--- abstract

TODO Abstract


--- middle

# Introduction

TODO Introduction


# Conventions and Definitions

{::boilerplate bcp14-tagged}

# KEM security properties

## IND-CCA

TODO. Explain adaptive attacks (Bleichenbacher) to explain passive security
      is not enough. Define IND-CCA.

## Binding properties

TODO. Refer to 2023/1933, 2024/702 for the various binding properties,
    and attacks.

## Security properties of hybrid KEMs

TODO. IND-CCA robustness

TODO. Component reuse.

## Recommended baseline

IND-CCA, LEAK+-BIND

# Combiners from literature

TODO. Refer to 2018/024, 2024/039, etc. and how these


# PQ/T hybrids

## X25519+Kyber768

## P384+MLKEM1024

### Encoding and sizes

P384+MLKEM1024 encapsulation key, decapsulation key, ciphertext and shared
secrets are all fixed length byte strings.

 Decapsulation key (private):
 : 3360 bytes

 Encapsulation key (public):
 : 1664 bytes

 Ciphertext:
 : 1664 bytes

 Shared secret:
 : 32 bytes

### Key generation

A P384+MLKEM1024 keypair (decapsulation key, encapsulation key) is generated
as follows.

~~~
def GenerateKeyPair():
  (pk_M, sk_M) = ML-KEM-1024.KeyGen()
  sk_E = P-384-KeyGen(32)
  pk_E = P-384-DH(sk_E, P384_BASE)
  return concat(sk_M, sk_E, pk_E), concat(pk_M, pk_E)
~~~

#### Key derivation

### Combiner

Given 32 byte strings `ss_M`, `ss_E`,
and 96 byte strings `ct_X`, `pk_X`, representing the
ML-KEM-1024 shared secret, P-384 shared secret, P-384 ciphertext
(ephemeral public key) and P-384 public key respectively, the 32 byte
combined shared secret is given by:

~~~
def Combiner(ss_M, ss_E, ct_E, pk_E):
    return SHA3-X(concat(
        # TBD
    ))
~~~

### Encapsulation

~~~
def Encapsulate(pk):
    # TBD
~~~

#### Derandomized

### Decapsulation

~~~
def Decapsulate(ct, sk):
    # TBD
~~~


## (P256+MLKEM768)


~~~

##


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

# Test vectors

## (P256+MLKEM768)

## X25519+MLKEM768

## P384+MLKEM1024

# Acknowledgments
{:numbered="false"}

TODO acknowledge.
