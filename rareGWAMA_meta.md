## rareGWAMA meta analysis

**Introduction to rareGWAMA**

### 0.File Preperation & Pre-process

This part is to create the necessity files and check the study validity. In general, the following files are needed: 
- Index File
- Summary statistics file for each study
- Imputation file for each study
- Principle components file
- Genomic control file

#### 0.1 Index File Creation
Index file is a file that can locate all data sets that would like to be meta-analyzed. A suggest format of index file can have the following format: 
```
Study01_name  Study01_summary_statistics_location Study01_imputation_file_location
Study02_name  Study02_summary_statistics_location Study03_imputation_file_location
Study03_name  Study03_summary_statistics_location Study03_imputation_file_location
Study04_name  Study04_summary_statistics_location Study04_imputation_file_location
...
```
By creating this file, it is easier to get access to each study's file without accidently modifying files. 

#### 0.2 Check Flip Variants

This part is necessary due to the fact that the reference allele and alternative allele may not be consistent across all studies. If that case happens, it is necessary to "flip" corresponding summary statistics, including: AF (alternative allele frequency), Z-score statistics etc. 

#### 0.3 PCs Calculation 

The calculation of PCs is based on MDS (multidimensioanl scaling) using allele frequency. For sanity check, we usually will merge our studies with 1000G project 5 ancesties' allele frequency, ie AFR_AF (African), AMR_AF (Ad Mixed Amrican),  EAS_AF (East Asian), EUR_AF (European), SAS_AF (South Asian). Merge criteria is based on "Chromosome_Position_Reference Allele_Alternative Allele", ie all four areas should be matched. Additionally, we will only include variants that exist in all studies. 

The input of MDS is a distance matrix. The definition of genetic distance based on allele frequency can be discribed as: 


#### 0.4 GC Value Calculation 

Genomic control values (GC)

Usually, we will calculate GC values for both rare variants and common variants. Rare variants are defined as MAF (Minor Allele Frquency) between 0.1% to 1%. While common varinats are defined as MAF no less than 1%: 
- Rare Variants: MAF>= 0.1% & MAF < 1%
- Common Variants: MAF>=1%


### 1.Basic Command

A typical command of running meta analysis using rareGWAMA is like: 

`rareGWAMA.single(score.stat.file,imp.qual.file,tabix.range=tabix.range,rmMultiAllelicSite=TRUE,impQualWeight=TRUE,
               impQual.lb=0.3,trans.ethnic=TRUE,af.pca=af.pca,gc=TRUE,
               lambda=lambda,maf.bin=maf.bin, memo.recalibrate = T)`


> * score.stat.file: a vector of string, each element is the address that points to each study's summary statistics
> * imp.qual.file: a vector of string, each element is the address that points to each study's imputation quality file. 
> * tabix.range: a string that indicates the tabix range of interest. 
> * rmMultiAllelicSite: a Boolean variable that indicating if multiallelic site should be removed. 
> * impQualWeight
> * impQual.lb: a numeric value from 0 to 1 to indicate the imputation quality lower bound 
> * trans.ethnic: a Boolean variable that indicate whether trans-ethnic meta-analysis should be performed. If set to true, then af.pca should also be provided. 
> * af.pca: a data frame that includes PCs for each study with the first column of 1, indicating intercept in the model. 
> * gc: a Boolean variable that indicate whether by-study genomic control should be performed. 
> * lambda: genomic control value matrix
> * maf.bin: 
> * memo.recalibrate: a calibrated version of MEMO model. Set these value to T all the time to get reliable results.

### 2.Input Files & Argument
All the score statistics files and imputation quality files should be tabix indexed.
#### Summary Statistics File
Each summary statistics file should have the following format:
```
CHROM   POS     REF     ALT     N_INFORMATIVE   AF      INFORMATIVE_ALT_AC      CALL_RATE       HWE_PVALUE      N_REF   N_HET   N_ALT   U_STAT  SQRT_V_STAT     ALT_EFFSIZE     PVALUE
1       10177   A       AC      2352    0.5     2352    1       0       0       2352    0       1.67496 2.51553 0.264695        0.505508
1       10235   T       TA      2352    0       0       1       1       2352    0       0       -0.108472       0.207841        -2.51104        0.601742
1       10352   T       TA      2352    0.5     2352    1       0       0       2352    0       0.665562        2.61389 0.0974122       0.799013
1       10539   C       A       2352    0       0       1       1       2352    0       0       -0.00020902     0.0626305       -0.0532862      0.997337
```
If you are using the results from rvtest, then the result is good to go. 

#### Imputation Quality File 
Each imputation quality file should have the following format: 
```
CHROM   POS     REF     ALT     Rsq
1       10177   A       AC      0.00581
1       10235   T       TA      0.00396
1       10352   T       TA      0.00608
1       10539   C       A       0.00154
1       10616   CCGCCGTTGCAAAGGCGCGCCG  C       0.02085
1       10642   G       A       0.00013
```




### 3.Results

#### 3.1 Results Summary
After running rareGWAMA.single function, a large list will be returned. In order to get a summary of the final results, we can use: 
> * res$res.formatted

#### 3.2 Manhattan Plot & QQ plot


#### 3.3 Tree Plot


For more details, please contact 

