DEXON DKG Protocol
===========================
### Parameter
* λ = One gossip time
* Signature = [BLS](https://en.wikipedia.org/wiki/Boneh%E2%80%93Lynn%E2%80%93Shacham)
* Curve = CurveFp382_2
* t = <img src="https://latex.codecogs.com/svg.latex?\inline%20\frac{1}{3}n+1" />

Phase 1 ID Registration 
-------
### @ T < 0

Each validator registers its ID with stack.

Phase 2 Secret Key Share Exchange
-------
### @ T = 0
Each validator `i` generates `n` (`n` = # of ID registered in phase 1) secret key shares (`SK_i,0, SK_i,1, ..., SK_i,n`) of order `t` and the secret key share is sent to the corresponding validator (`SK_i,j` is sent to validator `j`) via a secure channel.

Each validator `i` broadcasts the master public key (`MPK_i = {MPK_i,0, MPK_i,1, ..., MPK_i,t}`) of order `t` associated with the secret key shares.

~~Each validator `i` broadcasts public key shares (`PK_i,0, PK_i,1, ..., PK_i,n`) associated with secret key shares.~~

Phase 3 Complaint
-------
### @ T = λ
Each validator `i` calculates public key shares (`PK_0,i, PK_1,i, ..., PK_n,i`) using corresponding master public key (`PK_j,i = F(MPK_j, i)`).

Each validator `i` verifies if the secret key share `SK_i,j` is associated with the public key share of validator `j`, `PK_i,j`. If the verification fails, `i` broadcast complaint of `j`, `CMP_i,j`.

Phase 4 Rebroadcast Complaint
-------
### @ T = (λ, 2λ)
If CMP_i,j is received for first time, broadcast received CMP_i,j.

Phase 4 Sign with CSK
-------
### @ T = 2λ
If there are more than `t` complaints to validator `j` (<img src="https://latex.codecogs.com/svg.latex?\inline%20\sum_{i}%20CMP_{i,j}%20>%20t" /> (`i` : for all validator `i`)), then `j` is marked as **Disqualified**.

Each validator `i` determines the combined secret key, <img src="https://latex.codecogs.com/svg.latex?\inline%20CSK_{i}%20=%20\sum_{k}%20SK_{k,i}" /> (`k`: validator `k` is not marked as **Disqualified**)

Each validator `i` sign the message with `CSK_i` and broadcast the partial signature, `PSign_i`.

Each validator `i` determines the combined public key of validator `j`, <img src="https://latex.codecogs.com/svg.latex?\inline%20CPK_{j}%20=%20\sum_{k}%20PK_{k,j}" /> (`k`: validator `k` is not marked as **Disqualified**)

Phase 5 TSIG
-------
### @ T = (2λ, +inf)
If validator `i` is not **Disqualified**, verify `PSign_i` with `CPK_i`.

Collect more than `t` valid `PSign_i` and recover TSIG, `TSIG`.

Phase 6 Verify TSIG
-------
Determines the group public key, <img src="https://latex.codecogs.com/svg.latex?\inline%20GPK%20=%20\sum_{k}%20MPK_{k,0}" /> (`k`: validator `k` is not marked as **Disqualified**)
Verify `TSIG` with `GPK`.