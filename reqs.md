We'd like to share the outcome of the Hybrid KEM requirements design
team. First, our considerations distilled from the discussions
within the research group.

(1) There are valid but conflicting requirements; a single PQ/T
    hybrid KEM will not do.

(2) Given the recent work on binding properties, there is a general
    lack on clarity on KEM security properties.

(3) By its very nature, there are many choices that have to be made
    for a hybrid KEM. Without coordination, this will lead (and has
    led) to needlessly incompatible KEMs and duplicate effort.

(4) There are stakeholders that want to adopt some PQ/T hybrid,
    once NIST finishes ML-KEM this summer.

Hence, we propose that the CFRG produce a document "Hybrid PQ/T Key
Encapsulation Mechanisms", which will cover the following.

(A) Provide an overview of KEM security properties (IND-CCA,
    LEAK-BIND-K-PK, etc), as well as security properties unique to
    hybrid KEMs (component key material reuse between hybrid and
    non-hybrid uses or between multiple hybrids, one component is
    malicious while the other is honest, etc) with reference to literature,
    and put into context with real-world attacks. From that, give
    guidance on a sensible baseline.

(B) Provide a terse overview of well-reviewed techniques to safely
    combine primitives (whether KEM or DH), and which security properties
    are achieved given those of the constituents.

(C) Provide an initial number of explicit PQ/T hybrid KEMs using
    combiners from (2) that reach the baseline set in (1), and should
    include:
    
    (I)  a hybrid of P-256 and ML-KEM-768,
    (II)  a hybrid of X25519 and ML-KEM-768, and,
    (III) a hybrid of P-384 and ML-KEM-1024.
    
These hybrids should be accompanied by pseudocode and test vectors. 

The DT would be happy for the RG to omit C(I) above should there
not be significant implementations for which C(II) and C(III) are
hard. The DT did not attempt to survey implementations to determine
this.

There is demand for other hybrid variants that either use different
primitives (RSA, NTRU, Classic McEliece, FrodoKEM), parameters, or
that use a combiner optimized for a specific use case. The DT
recommends the work outlined in (C) is done in a first document,
and other use cases could be covered in subsequent documents.

TODO:
  - provide an outline/TOC for documents A & B
- provide formulae for C(I), C(II) and C(III) as a starting point for CFRG, analysis etc (??)
  - declare victory
  
  Plan as of 2024-06-18:
      - turn the above into slideware for ietf-120
      - ask for 20 min slot @ ietf-120 (5 mins pres, 15 chat)
      - Bas will take a peek at proposed I-D outline(s) for July 2nd
      - meet again July 2nd

