## rareGWAMA meta analysis

**Introduction to rareGWAMA**

### 1.Pre-request Files & Formats

A typical command of running meta analysis using rareGWAMA is like: 

> * rareGWAMA.single(score.stat.file,imp.qual.file,tabix.range=tabix.range,rmMultiAllelicSite=TRUE,impQualWeight=TRUE,
                        impQual.lb=0.3,trans.ethnic=TRUE,af.pca=af.pca,gc=TRUE,
                        lambda=lambda,maf.bin=maf.bin, memo.recalibrate = T)


> * the score.stat.file: The statistics summary files, like:

```
CHROM   POS     REF     ALT     N_INFORMATIVE   AF      INFORMATIVE_ALT_AC      CALL_RATE       HWE_PVALUE      N_REF   N_HET   N_ALT   U_STAT  SQRT_V_STAT     ALT_EFFSIZE     PVALUE
1       10177   A       AC      2352    0.5     2352    1       0       0       2352    0       1.67496 2.51553 0.264695        0.505508
1       10235   T       TA      2352    0       0       1       1       2352    0       0       -0.108472       0.207841        -2.51104        0.601742
1       10352   T       TA      2352    0.5     2352    1       0       0       2352    0       0.665562        2.61389 0.0974122       0.799013
1       10539   C       A       2352    0       0       1       1       2352    0       0       -0.00020902     0.0626305       -0.0532862      0.997337
```


### 2.Running rareGWAMA in R


### 3.Results





For more details, please contact 

