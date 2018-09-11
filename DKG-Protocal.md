DEXON DKG Protocol (draft)
===========================
Phase 1
-------
ID Registration
Each validator broadcasts its ID to the network.

Phase 2
-------
Secret Key Share Exchange
Each validator i generates n (n = # of ID registered in phase 1) secret key shares (SK_i,0, SK_i,1, ..., SK_i,n) and the secret key share is send to corresponding validator (SK_i,j is send to Validator j) via secure channel.

Phase 3
-------
Common Secret Key Share
Each validator i determines the common secret key share CSK{SK_k,i} (k : for all validator j, SK_k,j is received and verified)

Phase 4
-------
TSIG
Each validator i sign the message with CSK and send the signature, Sign_i, to TSIG protocol.