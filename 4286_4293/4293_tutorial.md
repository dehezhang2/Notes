# CS4293 Tutorial

## Tutorial 2

* q1: Known plaintext attack
* q2: Ciphertext only attack
* q3: Chose plaintext attack

* q4: `a` is larger
  $$
  2^{256} = (2^{10})^{25.6} \approx (10^{3})^{25.6}
  $$

* q5: It is secure for passive attacker, but not secure for active attacker

  * **Also need to provide a nonce to avoid reply attack **
  * **The reuse of the same key for encryption and authentication may lead to leaking information**

* q6: False. For ECB mode, same plaintext will result in the same ciphertext if we use the same key

* q7: **True, for CBC mode, the ciphertext will be dependent on the previous blocks, M1 and M2 have different first blocks**

## Tutorial 3

* q1
  * Confidentiality
  * Confidentiality
  * Integrity
  * Availability
  * Confidentiality
  * **Integrity**: Virus is planted and your friend’s system is being modified in background;
* q2:
  * C: Any kinds of transaction should not be accessed by others
  * I: The amount of transaction should not be changed
  * A: The transfer service should be available
* q3: The certificate issued by CA
  * **M, Signature = Epriv_Bob(M), Certificate = Epriv_CA(pub_Bob).**
  * **Signature = Epriv_Bob(H(M)) also works, where H() is a hash function.**
* q4:
  * Strength of symmetric encryption:
    * Computation is fast
    * Need shorter key to provide similar security for asymmetric key
    * symmetric-key encryption is easier to understand by an non-expert than public- key encryption
  * Weakness of symmetric encryption
    * Each pairs of users share a key, need to manage many keys
  * Strength of asymmetric encryption
    * Each one has a private key and a public key, the number of keys need to manage is linear
  * Weakness of asymmetric encryption
    * Computation is slow
    * Need longer key to provide similar security for asymmetric key

* q5: 1character = 1 byte
  $$
  {2^{1.25t} \over 2^{8t}} = 2^{-6.75t}
  $$

* q6: False. The counter mode does not have block dependency

* q7: True. 

## Tutorial 4

* q1: The first one is more expensive
  * 9 square, 9 multiply
  * 10 square, 1 multiply
* q2: 
  * $Z_n$: set of integers less than $n$ and larger than or equal to $0$
  * $Z_n^*$: The positive integer less than $n$ and coprime with $n$
* q3: No, because p-1 and q-1 are even, e should be coprime to (p-1)(q-1)
* q4: $4^3\ mod\ 77 = 64$
* q5: $ \phi = 100*102 = 10200$ , $20^{3}\ mod\ 10403 = 8000$

## Tutorial 5

* q1: 
  * What the user has: token
  * What the user is (biometrics)
  * What the user knows (pwd)
  * What the user does (dynamic biometrics)
* q2: 



* q3: hash password with a random salt
* q4: 
* q5: 