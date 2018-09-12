DEXON DKG Protocol
===========================
### Parameter
* λ = One gossip time
* Signature = [BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham)
* Curve = CurveFp382_2

Phase 1 ID Registration 
-------
### @ T < 0

Each validator register its ID with stack.

Phase 2 Secret Key Share Exchange
-------
### @ T = 0
Each validator `i` generates `n` (`n` = # of ID registered in phase 1) secret key shares (`SK_i,0, SK_i,1, ..., SK_i,n`) of order `t` and the secret key share is sent to the corresponding validator (`SK_i,j` is sent to validator `j`) via a secure channel.

Each validator `i` broadcast the master public key (`PK_i`) associated with the secret key shares.

Phase 3 Complaint
-------
### @ T = 2λ
Each validator `i` verify if the secret key share `SK_i,j` is associated with the master public key of validator `j` `PK_j`. If the verification fails, `i` broadcast complaint of `j`, `CMP_i,j`.

Phase 4 Disqualify Byzantine Node
-------
### @ T = (2λ, 4λ)
If there are more then `t` complaints to validator `j` (<img src="https://latex.codecogs.com/svg.latex?%5Cinline%20%5Csum_%7Bi%7D%20CMP_%7Bi%2Cj%7D%20%3E%20t" /> (`i` : for all validator `i`)), then `j` is marked as **Disqualified**.

Each validator `i` determines the combined secret key, `<img src="https://latex.codecogs.com/gif.latex?%5Cinline%20CSK_%7Bi%7D%20%3D%20%5Csum_%7Bk%7D%20SK_%7Bk%2Ci%7D" />` (`k`: validator `k` is not marked as **Disqualified**)

Each validator `i` determines the combined public key for all validator `j`, `CPK_j = SUM_k PK_k,j` (`k`: validator `k` is not marked as **Disqualified**)

Phase 5 Sign with CSK
-------
### @ T = 4λ
Each validator `i` sign the message with `CSK_i` and broadcast the signature, `Sign_i`.

Phase 6 TSIG
-------
### @ T = (4λ, +inf)
Verify `Sign_i` with `CPK_i`.

Collect more than `t` valid `Sign_i` and recover TSIG.