### types

SIP : integer
LIP : string

3 BEN 3 : SIX
3 BEN "3" : NIX
3 BELIS "3" : SIX
3 BELIS SIP "3" : SIX
3 BELIS LIP "3" : NIX

5 BONIN 3 VAS 9 : SIX
5 BONIN 3 VAS "9" : NIX
5 BONIT 2 VAS 8 : NIX
5 BONIT 2 VAS "8" : SIX

IAP - action
TIXIAP - foreach loop
BONIAP - for loop, range loop

[3, 4, 5] BELIN [6, 8 ,10] : SIX
[3, 4, 5] BELIN [6, 8, "10"] : NIX