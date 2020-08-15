## rareGWAMA meta analysis

**Introduction to rareGWAMA**

### 0.File Preperation & Pre-process

#### Index File Creation

#### Check Flip Variants

#### PCs Calculation 

#### GC Value Calculation 




### 1.Pre-request Files & Formats

A typical command of running meta analysis using rareGWAMA is like: 

> * rareGWAMA.single(score.stat.file,imp.qual.file,tabix.range=tabix.range,rmMultiAllelicSite=TRUE,impQualWeight=TRUE,
               impQual.lb=0.3,trans.ethnic=TRUE,af.pca=af.pca,gc=TRUE,
               lambda=lambda,maf.bin=maf.bin, memo.recalibrate = T)


> * score.stat.file: a vector of string, each element is the address that points to each study's summary statistics

Each summary statistics file should have the following format:

```
CHROM   POS     REF     ALT     N_INFORMATIVE   AF      INFORMATIVE_ALT_AC      CALL_RATE       HWE_PVALUE      N_REF   N_HET   N_ALT   U_STAT  SQRT_V_STAT     ALT_EFFSIZE     PVALUE
1       10177   A       AC      2352    0.5     2352    1       0       0       2352    0       1.67496 2.51553 0.264695        0.505508
1       10235   T       TA      2352    0       0       1       1       2352    0       0       -0.108472       0.207841        -2.51104        0.601742
1       10352   T       TA      2352    0.5     2352    1       0       0       2352    0       0.665562        2.61389 0.0974122       0.799013
1       10539   C       A       2352    0       0       1       1       2352    0       0       -0.00020902     0.0626305       -0.0532862      0.997337
```
If you are using the results from , then it

> * imp.qual.file: a vector of string, each element is the address that points to each study's imputation quality file. 

The order should be the same as score.stat.file.

Each imputation quality file should have the following format: 

> * tabix.range: a string that indicates the tabix range of interest

> * impQual.lb: a numeric value from 0 to 1 to indicate the imputation quality lower bound 

> * trans.ethnic: a Boolean variable that indicate whether trans-ethnic meta-analysis should be performed. 

> * af.pca: a data frame that includes PCs for each study. 

Each row represents one study. The order should be the same as score.stat.file. Each column should be one PC. Additionally, a column of 1 should be included if you would like to include an intercept. This parameter will only be effective if trans.ethnic = T

A typical 

### 2.Running rareGWAMA in R


### 3.Results

After running rareGWAMA.single function, a large list will be returned. In order to get a summary of the final results, we can use: 
> * res$res.formatted




For more details, please contact 

