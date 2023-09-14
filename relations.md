### relation & comparison
BEN - equal, exact match, stuck
NIBEN - inequal
BEK - greater than
BENK - equal or greater than
BES - lower than
BENS - equal or lower than

BON - range, array
BONI - to insert, place between
BONIN - item in range, between
BONIT - item out of range

BEL - has relation
BELIN - parallel, synchronized, aligned, means
BELIT - non-parallel, non-aligned, async
BELIS - crossing, conflicting, similar, in conjunction, common, partial match
NIBEL - non-related


### types

SIP : integer
LIP : string

3 BEN 3 : SIX
3 BEN "3" : NIX

3 BENS 4 : SIX
3 BENS "4" : NIX

3 BELIS "3" : SIX
3 BELIS SIP "3" : SIX  
3 BELIS LIP "3" : NIX
"5" BELIS LIP "9" : SIX // check on type string

5 BONIN 3 VAS 9 : SIX
5 BONIN 3 VAS "9" : NIX
5 BONIT 2 VAS 8 : NIX
5 BONIT 2 VAS "8" : SIX

IAP - action
TIXIAP - foreach loop, range loop
BONIAP - for loop

[3, 4, 5] BELIN [6, 8 ,10] : SIX
[3, 4, 5] BELIN [6, 8, "10"] : NIX
[3, 4, 5] BELIS [6, 8, "10"] : SIX
[3, 4, 5] BELIS SIP [6, 8, "10"] : NIX
[3, 4, 5] BELIS LIP [9, 8, 4] : SIX


// check on range size
[3, 4, 5] BELIS SI [9, 8, 4] : SIX
[3, 4, 5] BELIS SI [3, 4, 5, 6] : NIX