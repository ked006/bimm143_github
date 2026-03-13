# Class 19: Mutation Project


I downloaded my sequences and loaded them onto my working/project
directory.

I ran a BLASTp search against REFSEQ_Protein filtered to human only: JOB
ID:

job title: healthy WT RID: V39DACND014 – Official symbol:TP53 – Official
full name: tumor protein p53 protein coding –\> gene type

> Q2. What are the tumor specific mutations in this particular case
> (e.g. A130V)?

The tumor specific mutations are at: L137V, V147E, S185R, P190Y

``` r
library (bio3d)
```

    Warning: package 'bio3d' was built under R version 4.4.3

``` r
a <- read.fasta("A18544481_mutant_seq.fa")
```

``` r
attributes(a)
```

    $names
    [1] "id"   "ali"  "call"

    $class
    [1] "fasta"

``` r
a$ali
```

                 [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12]
    wt_healthy   "M"  "E"  "E"  "P"  "Q"  "S"  "D"  "P"  "S"  "V"   "E"   "P"  
    mutant_tumor "M"  "E"  "E"  "P"  "Q"  "S"  "D"  "P"  "S"  "V"   "E"   "P"  
                 [,13] [,14] [,15] [,16] [,17] [,18] [,19] [,20] [,21] [,22] [,23]
    wt_healthy   "P"   "L"   "S"   "Q"   "E"   "T"   "F"   "S"   "D"   "L"   "W"  
    mutant_tumor "P"   "L"   "S"   "Q"   "E"   "T"   "F"   "S"   "D"   "L"   "W"  
                 [,24] [,25] [,26] [,27] [,28] [,29] [,30] [,31] [,32] [,33] [,34]
    wt_healthy   "K"   "L"   "L"   "P"   "E"   "N"   "N"   "V"   "L"   "S"   "P"  
    mutant_tumor "K"   "L"   "L"   "P"   "E"   "N"   "N"   "V"   "L"   "S"   "P"  
                 [,35] [,36] [,37] [,38] [,39] [,40] [,41] [,42] [,43] [,44] [,45]
    wt_healthy   "L"   "P"   "S"   "Q"   "A"   "M"   "D"   "D"   "L"   "M"   "L"  
    mutant_tumor "L"   "P"   "S"   "Q"   "A"   "M"   "D"   "D"   "L"   "M"   "L"  
                 [,46] [,47] [,48] [,49] [,50] [,51] [,52] [,53] [,54] [,55] [,56]
    wt_healthy   "S"   "P"   "D"   "D"   "I"   "E"   "Q"   "W"   "F"   "T"   "E"  
    mutant_tumor "S"   "P"   "D"   "D"   "I"   "E"   "Q"   "W"   "F"   "T"   "E"  
                 [,57] [,58] [,59] [,60] [,61] [,62] [,63] [,64] [,65] [,66] [,67]
    wt_healthy   "D"   "P"   "G"   "P"   "D"   "E"   "A"   "P"   "R"   "M"   "P"  
    mutant_tumor "D"   "P"   "G"   "P"   "D"   "E"   "A"   "P"   "R"   "M"   "P"  
                 [,68] [,69] [,70] [,71] [,72] [,73] [,74] [,75] [,76] [,77] [,78]
    wt_healthy   "E"   "A"   "A"   "P"   "P"   "V"   "A"   "P"   "A"   "P"   "A"  
    mutant_tumor "E"   "A"   "A"   "P"   "P"   "V"   "A"   "P"   "A"   "P"   "A"  
                 [,79] [,80] [,81] [,82] [,83] [,84] [,85] [,86] [,87] [,88] [,89]
    wt_healthy   "A"   "P"   "T"   "P"   "A"   "A"   "P"   "A"   "P"   "A"   "P"  
    mutant_tumor "A"   "P"   "T"   "P"   "A"   "A"   "P"   "A"   "P"   "A"   "P"  
                 [,90] [,91] [,92] [,93] [,94] [,95] [,96] [,97] [,98] [,99] [,100]
    wt_healthy   "S"   "W"   "P"   "L"   "S"   "S"   "S"   "V"   "P"   "S"   "Q"   
    mutant_tumor "S"   "W"   "P"   "L"   "S"   "S"   "S"   "V"   "P"   "S"   "Q"   
                 [,101] [,102] [,103] [,104] [,105] [,106] [,107] [,108] [,109]
    wt_healthy   "K"    "T"    "Y"    "Q"    "G"    "S"    "Y"    "G"    "F"   
    mutant_tumor "K"    "T"    "Y"    "Q"    "G"    "S"    "Y"    "G"    "F"   
                 [,110] [,111] [,112] [,113] [,114] [,115] [,116] [,117] [,118]
    wt_healthy   "R"    "L"    "G"    "F"    "L"    "H"    "S"    "G"    "T"   
    mutant_tumor "R"    "L"    "G"    "F"    "L"    "H"    "S"    "G"    "T"   
                 [,119] [,120] [,121] [,122] [,123] [,124] [,125] [,126] [,127]
    wt_healthy   "A"    "K"    "S"    "V"    "T"    "C"    "T"    "Y"    "S"   
    mutant_tumor "A"    "K"    "S"    "V"    "T"    "C"    "T"    "Y"    "S"   
                 [,128] [,129] [,130] [,131] [,132] [,133] [,134] [,135] [,136]
    wt_healthy   "P"    "A"    "L"    "N"    "K"    "M"    "F"    "C"    "Q"   
    mutant_tumor "P"    "A"    "L"    "N"    "K"    "M"    "F"    "C"    "Q"   
                 [,137] [,138] [,139] [,140] [,141] [,142] [,143] [,144] [,145]
    wt_healthy   "L"    "A"    "K"    "T"    "C"    "P"    "V"    "Q"    "L"   
    mutant_tumor "V"    "A"    "K"    "T"    "C"    "P"    "V"    "Q"    "L"   
                 [,146] [,147] [,148] [,149] [,150] [,151] [,152] [,153] [,154]
    wt_healthy   "W"    "V"    "D"    "S"    "T"    "P"    "P"    "P"    "G"   
    mutant_tumor "W"    "E"    "D"    "S"    "T"    "P"    "P"    "P"    "G"   
                 [,155] [,156] [,157] [,158] [,159] [,160] [,161] [,162] [,163]
    wt_healthy   "T"    "R"    "V"    "R"    "A"    "M"    "A"    "I"    "Y"   
    mutant_tumor "T"    "R"    "V"    "R"    "A"    "M"    "A"    "I"    "Y"   
                 [,164] [,165] [,166] [,167] [,168] [,169] [,170] [,171] [,172]
    wt_healthy   "K"    "Q"    "S"    "Q"    "H"    "M"    "T"    "E"    "V"   
    mutant_tumor "K"    "Q"    "S"    "Q"    "H"    "M"    "T"    "E"    "V"   
                 [,173] [,174] [,175] [,176] [,177] [,178] [,179] [,180] [,181]
    wt_healthy   "V"    "R"    "R"    "C"    "P"    "H"    "H"    "E"    "R"   
    mutant_tumor "V"    "R"    "R"    "C"    "P"    "H"    "H"    "E"    "R"   
                 [,182] [,183] [,184] [,185] [,186] [,187] [,188] [,189] [,190]
    wt_healthy   "C"    "S"    "D"    "S"    "D"    "G"    "L"    "A"    "P"   
    mutant_tumor "C"    "S"    "D"    "R"    "D"    "G"    "L"    "A"    "Y"   
                 [,191] [,192] [,193] [,194] [,195] [,196] [,197] [,198] [,199]
    wt_healthy   "P"    "Q"    "H"    "L"    "I"    "R"    "V"    "E"    "G"   
    mutant_tumor "P"    "Q"    "H"    "L"    "I"    "R"    "V"    "E"    "G"   
                 [,200] [,201] [,202] [,203] [,204] [,205] [,206] [,207] [,208]
    wt_healthy   "N"    "L"    "R"    "V"    "E"    "Y"    "L"    "D"    "D"   
    mutant_tumor "N"    "L"    "R"    "V"    "E"    "Y"    "L"    "D"    "D"   
                 [,209] [,210] [,211] [,212] [,213] [,214] [,215] [,216] [,217]
    wt_healthy   "R"    "N"    "T"    "F"    "R"    "H"    "S"    "V"    "V"   
    mutant_tumor "R"    "N"    "T"    "F"    "R"    "H"    "S"    "V"    "V"   
                 [,218] [,219] [,220] [,221] [,222] [,223] [,224] [,225] [,226]
    wt_healthy   "V"    "P"    "Y"    "E"    "P"    "P"    "E"    "V"    "G"   
    mutant_tumor "V"    "P"    "Y"    "E"    "P"    "P"    "E"    "V"    "G"   
                 [,227] [,228] [,229] [,230] [,231] [,232] [,233] [,234] [,235]
    wt_healthy   "S"    "D"    "C"    "T"    "T"    "I"    "H"    "Y"    "N"   
    mutant_tumor "S"    "D"    "C"    "T"    "T"    "I"    "H"    "Y"    "N"   
                 [,236] [,237] [,238] [,239] [,240] [,241] [,242] [,243] [,244]
    wt_healthy   "Y"    "M"    "C"    "N"    "S"    "S"    "C"    "M"    "G"   
    mutant_tumor "Y"    "M"    "C"    "N"    "S"    "S"    "C"    "M"    "G"   
                 [,245] [,246] [,247] [,248] [,249] [,250] [,251] [,252] [,253]
    wt_healthy   "G"    "M"    "N"    "R"    "R"    "P"    "I"    "L"    "T"   
    mutant_tumor "G"    "M"    "N"    "R"    "R"    "P"    "I"    "L"    "T"   
                 [,254] [,255] [,256] [,257] [,258] [,259] [,260] [,261] [,262]
    wt_healthy   "I"    "I"    "T"    "L"    "E"    "D"    "S"    "S"    "G"   
    mutant_tumor "I"    "I"    "T"    "L"    "E"    "D"    "S"    "S"    "G"   
                 [,263] [,264] [,265] [,266] [,267] [,268] [,269] [,270] [,271]
    wt_healthy   "N"    "L"    "L"    "G"    "R"    "N"    "S"    "F"    "E"   
    mutant_tumor "N"    "L"    "L"    "G"    "R"    "N"    "S"    "F"    "E"   
                 [,272] [,273] [,274] [,275] [,276] [,277] [,278] [,279] [,280]
    wt_healthy   "V"    "R"    "V"    "C"    "A"    "C"    "P"    "G"    "R"   
    mutant_tumor "V"    "R"    "V"    "C"    "A"    "C"    "P"    "G"    "R"   
                 [,281] [,282] [,283] [,284] [,285] [,286] [,287] [,288] [,289]
    wt_healthy   "D"    "R"    "R"    "T"    "E"    "E"    "E"    "N"    "L"   
    mutant_tumor "D"    "R"    "R"    "T"    "E"    "E"    "E"    "N"    "L"   
                 [,290] [,291] [,292] [,293] [,294] [,295] [,296] [,297] [,298]
    wt_healthy   "R"    "K"    "K"    "G"    "E"    "P"    "H"    "H"    "E"   
    mutant_tumor "R"    "K"    "K"    "G"    "E"    "P"    "H"    "H"    "E"   
                 [,299] [,300] [,301] [,302] [,303] [,304] [,305] [,306] [,307]
    wt_healthy   "L"    "P"    "P"    "G"    "S"    "T"    "K"    "R"    "A"   
    mutant_tumor "L"    "P"    "P"    "G"    "S"    "T"    "K"    "R"    "A"   
                 [,308] [,309] [,310] [,311] [,312] [,313] [,314] [,315] [,316]
    wt_healthy   "L"    "P"    "N"    "N"    "T"    "S"    "S"    "S"    "P"   
    mutant_tumor "L"    "P"    "N"    "N"    "T"    "S"    "S"    "S"    "P"   
                 [,317] [,318] [,319] [,320] [,321] [,322] [,323] [,324] [,325]
    wt_healthy   "Q"    "P"    "K"    "K"    "K"    "P"    "L"    "D"    "G"   
    mutant_tumor "Q"    "P"    "K"    "K"    "K"    "P"    "L"    "D"    "G"   
                 [,326] [,327] [,328] [,329] [,330] [,331] [,332] [,333] [,334]
    wt_healthy   "E"    "Y"    "F"    "T"    "L"    "Q"    "I"    "R"    "G"   
    mutant_tumor "E"    "Y"    "F"    "T"    "L"    "Q"    "I"    "R"    "G"   
                 [,335] [,336] [,337] [,338] [,339] [,340] [,341] [,342] [,343]
    wt_healthy   "R"    "E"    "R"    "F"    "E"    "M"    "F"    "R"    "E"   
    mutant_tumor "R"    "E"    "R"    "F"    "E"    "M"    "F"    "R"    "E"   
                 [,344] [,345] [,346] [,347] [,348] [,349] [,350] [,351] [,352]
    wt_healthy   "L"    "N"    "E"    "A"    "L"    "E"    "L"    "K"    "D"   
    mutant_tumor "L"    "N"    "E"    "A"    "L"    "E"    "L"    "K"    "D"   
                 [,353] [,354] [,355] [,356] [,357] [,358] [,359] [,360] [,361]
    wt_healthy   "A"    "Q"    "A"    "G"    "K"    "E"    "P"    "G"    "G"   
    mutant_tumor "A"    "Q"    "A"    "G"    "K"    "E"    "P"    "G"    "G"   
                 [,362] [,363] [,364] [,365] [,366] [,367] [,368] [,369] [,370]
    wt_healthy   "S"    "R"    "A"    "H"    "S"    "S"    "H"    "L"    "K"   
    mutant_tumor "S"    "R"    "A"    "H"    "S"    "S"    "H"    "L"    "K"   
                 [,371] [,372] [,373] [,374] [,375] [,376] [,377] [,378] [,379]
    wt_healthy   "S"    "K"    "K"    "G"    "Q"    "S"    "T"    "S"    "R"   
    mutant_tumor "S"    "K"    "K"    "G"    "Q"    "S"    "T"    "S"    "R"   
                 [,380] [,381] [,382] [,383] [,384] [,385] [,386] [,387] [,388]
    wt_healthy   "H"    "K"    "K"    "L"    "M"    "F"    "K"    "T"    "E"   
    mutant_tumor "H"    "K"    "K"    "L"    "M"    "F"    "K"    "T"    "E"   
                 [,389] [,390] [,391] [,392] [,393]
    wt_healthy   "G"    "P"    "D"    "S"    "D"   
    mutant_tumor "G"    "P"    "D"    "S"    "D"   

We can score conservation per sequence position

``` r
score <- conserv(a)
mutation.position <- which( score != 1)
mutation.position
```

    [1] 137 147 185 190

``` r
a$ali[, 137]
```

      wt_healthy mutant_tumor 
             "L"          "V" 

``` r
a$ali[, 147]
```

      wt_healthy mutant_tumor 
             "V"          "E" 

``` r
a$ali[, 185]
```

      wt_healthy mutant_tumor 
             "S"          "R" 

``` r
a$ali[, 190]
```

      wt_healthy mutant_tumor 
             "P"          "Y" 

``` r
paste0(a$ali[1, mutation.position],
       mutation.position,
       a$ali[2, mutation.position])
```

    [1] "L137V" "V147E" "S185R" "P190Y"

What PFAM domain do these mutations reside in?

We can use HMMER at the EBI (if it works) to find this information:

OR we can use UniProt

> Q3. Do your mutations cluster to any particular domain and if so give
> the name and PFAM id of this domain? Alternately note whether your
> protein is single domain and provide it’s PFAM id/accession and name
> (e.g. PF00613 and PI3Ka).
