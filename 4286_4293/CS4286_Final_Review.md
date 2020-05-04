# CS4286 Final Review

[TOC]

## Lecture 06: Authentication

### Entity Authentication

* Autentication types

  * Stand-alone computer with physically secure connection: Simple
  * Over a network: Much more complex
    * Interception
    * Replay

* One-way authentication over an open network & Attack schemes

  * Scheme I 
    $$
    Alice \rightarrow Email\ Server: Username, password
    $$

    * **Masquerade/Replay Attack**: Eavesdropper can intercept Alice’s login information and use it to logon to the Email server

  * Scheme II
    $$
    (1)\ Alice \leftarrow Email\ Server: PK, Cert_{server} \\
    (2)\ Alice \color{red}{\rightarrow} Email\ Server: E_{PK}(Username, password) (secure\ channel) \\
    or \\
    (1)\ Alice \color{red}{\rightarrow} Email\ Server: Username, h(password) \\
    $$

    * **Replay Attack**: Adversary replays $E_{PK}$ or $h$ 

  * Scheme III: Challenge and responce
    $$
    Alice \leftarrow Email\ Server: N \\
    Alice \rightarrow Email\ Server: F(passwd, N) \\
    $$

    * Challenge $N$: Nonce (number used only once, does not need to be a random number)
    * Response $F(passwd, N)$: $F$ is a one-way function and $passwd$ is the password of Alice
      * $F$ can be hash or block cipher
    * Only Alice and the Email Server know the valud of the password. Hence only Alice can provide the correct responce to the Email Server. 

* Types of Challenge and response mechanisms

  * Hash function
    $$
    Alice(K_{AB}) \leftarrow Bob(K_{AB}):Nonce \\
    Alice(K_{AB}) \rightarrow Bob(K_{AB}):h(K_{AB}, Nonce) \\
    $$

  * MAC
    $$
    Alice(K_{AB}) \leftarrow Bob(K_{AB}):Nonce \\
    Alice(K_{AB}) \rightarrow Bob(K_{AB}):MAC(K_{AB}, Nonce) \\
    $$

  * Symmetric Encryption
    $$
    Alice(K_{AB}) \leftarrow Bob(K_{AB}):Nonce \\
    Alice(K_{AB}) \rightarrow Bob(K_{AB}):Enc(K_{AB}, Nonce)\ or\\
    Alice(K_{AB}) \leftarrow Bob(K_{AB}):Enc(K_{AB}, Nonce) \\
    Alice(K_{AB}) \rightarrow Bob(K_{AB}):Nonce \\
    $$

  * Asymmetric Encryption
    $$
    Alice(K_{AB}) \leftarrow Bob(K_{AB}):Nonce \\
    Alice(K_{AB}) \rightarrow Bob(K_{AB}):[Nonce]_{Alice}\ or\\
    Alice(K_{AB}) \leftarrow Bob(K_{AB}): \{Nonce\}_{Alice} \\
    Alice(K_{AB}) \rightarrow Bob(K_{AB}):Nonce \\
    $$

    * Assumptions and definitions
      * $\{\}$ represents public key encryption, $[]$ represents digital signature.
      * We assume the public keys are certified. 

* Entity Authentication: A sequence of messages passed between a claimant and a verifier designed to confirm that identity of the claimant. 

  * Terminologies: 
    * Claimant: An entity claiming an identity. (Google Server)
    * Principal: The identity claimed by a claimant. (Server of google.com)
    * Verifier: The entity verifying a claim. (browser)
  * Types:
    * Unilateral authentication: Only one entity is authenticated to another entity
    * Mutual authentication: Both entities are identified with each other
  * Requirements:
    * Origin authentication: Messages came from the principal
      * Message Authentication Codes (MACs)
      * Digital Signature Schemes
      * Symmetric Encryption (does not provides origin authentication without additional features => the verifier knows the expected content and format of the message)
    * Freshness: Messages have been recently generated

* 

## Lecture 07: Key Management

 