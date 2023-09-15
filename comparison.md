### comparison

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

### relation

BEL - has relation
BELIN - parallel, synchronized, aligned, means
BELIT - non-parallel, non-aligned, async
BELIS - crossing, conflicting, similar, in conjunction, common, partial match
BELÖN - factor
NIBEL - non-related


### types

SIP : integer, float
LIP : string

### equality check

3 BEN 3 : SIX
3 BEN "3" : NIX
"A" BEN "A" : SIX

### loose check on equality, cross

3 BELIS "3" : SIX // cross on value
"3" BELIS "5" : SIX // cross on type string
3 BELIS 5 : SIX // cross on type int
3 BELIS "7" : NIX // completely different, both on type and value

3 BELIS SIP "3" : SIX  // value cross
3 BELIS LIP "3" : NIX // type no cross
"5" BELIS LIP "9" : SIX // type cross

### comparison checks

3 BENS 4 : SIX
3 BENS "4" : NIX

5 BONIN 3 VAS 9 : SIX
5 BONIN 3 VAS "9" : NIX
5 BONIT 2 VAS 8 : NIX
5 BONIT 2 VAS "8" : SIX

## range checks

### check on parallel

[3, 4, 5] BELIN [8, 9, 10] : 3 // parallel
[3, 4, 5] BELIN [8, 9, "10"] : 0
[3, 4, 5] BELIN [6, 7, 8, 9, 10] : 3

[3, 4, 5] BELIT [6, 7, 8] : 3

[4, 4, 4, 6, 2] BELIN [5, 5, 5, 7, 3, 8] : 5
[4, 4, 4, 6, 2] BELIN [8, 5, 5, 5, 7, 3] : 5

[4, 4, 4, 6, 2] BELIN [8, 5, 5, 5, 7, 3] BENK 3 : 5
[4, 4, 4, 6, 2] BELIN [8, 5, 5, 5, 7, 3] BENK 6 : 0 // min. 6 points to match


### check on type/size on parallel
[3, 4, 5] BELIN SIP [8, 9, "10"] : 3

[3, 4, 5] BELIN BEN [6, 7, 8, 9, 10] : 0 // due to array size. Most strict check.

[3, 4, 5] BELIN BEN [6, 7, 8] : 3
[3, 4, 5] BEN [6, 7, 8] : NIX

// all range checks on BEN is a NIX, except 2 identical ranges
[3, 4, 5] BEN [3, 4, 5] : SIX

### check on cross/match

[3, 4, 5] BELIS [6, 7, 8] : 0
[3, 4, 5] BELIS [1, 2, "5"] : 0
[3, 4, 5] BELIS [1, 5, 9] : 1 // one matching element

### check on type on cross/match

[3, 4, 5] BELIS SIP [1, 2, "5"] : 1
[3, 4, 5, 8] BELIS SIP [9, 8, 4] : 2

### check on range size

[3, 4, 5] BELIS SI [9, 8, 7] : SIX
[3, 4, 5] BELIS SI [3, 4, 5, 6] : NIX

### string check on all integer ranges

[3, "4", 5] BELIS LIP ["1", 2, "7", 8] : 1

### with number of matches check

[1, 2, 3, 4, 5] BELIS [3, 4, 5, 6, 7] BEK 2 : SIX

[1, 2, 3, 4, 5] BELIS [3, 4, 5, 6, 7] BEN 3 : SIX

[1, 2, 3, 4, 5] BELIS [3, 4, 5, 6, 7] BEN "3" : NIX

### factor check

[3, 4, 5] BELÖN [6, 8, 10, 12, 14] : 2

[3, 4, 5] BELÖN [6, 8, "10"] : 0

[3, 4, 5] BELÖN [6, 8, 10, 15] : 0

### check on type on factor

[3, 4, 5] BELÖN SIP [4.5, 6, "7.5"] : 1.5

[3, 4, 5] BELÖN BEN [6, 8, 10, 12, 14] : 0

### float check

4 BEN 4.000000 : SIX
4 BEN 4.000001 : NIX

4 BES 4.000001 : SIX