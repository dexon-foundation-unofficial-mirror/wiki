DEXON DKG Protocol (draft)
===========================
Phase 1 ID Registration
-------
Each validator broadcasts its ID to the network.

Phase 2 Secret Key Share Exchange
-------
Each validator i generates n (n = # of ID registered in phase 1) secret key shares (SK_i,0, SK_i,1, ..., SK_i,n) and the secret key share is sent to each validator (SK_i,j is sent to Validator j) via a secure channel.
Each validator i broadcast the master public key (PK_i) associated with the secret key shares.
Each validator i verify if the secret key share SK_i,j is associated with the master public key of validator j PK_i. If the verification fails, i broadcast complaint of j CMP_i,j.

Phase 3 Disqualify Byzantine Node
-------
If there are more then t complaint to validator j (SUM_i CMP_i,j > t), the j is marked as 'Disqualified'.
Each validator i determines the common secret key share CSK{SK_k,i} (k : validator k is not marked as 'Disqualified')

Phase 4 Sign with CSK
-------
Each validator i sign the message with CSK and broadcast the signature, Sign_i.

Phase 5 TSIG
-------
Collect more than t Sign_i and recover TSIG.