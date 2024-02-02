# tfsites.CompareEnhancers v1

**Author(s):** Joe Solvason  

**Contact:** Joe Solvason (solvason@eng.ucsd.edu)

**Adapted as a GenePattern Module by:** Ted Liefeld (jliefeld@cloud.ucsd.edu)

**Task Type:** Transciption factor analysis

**LSID:**  urn:lsid:genepattern.org:module.analysis:00448


## Introduction

`compareSeqs` reports the differences and similarities in the transcription factor binding sites between two DNA sequences. Multiple transcription factors can be analyzed. This tool shows whether the binding sites across both sequences are shared, or distinct to one of the sequences. 

 
## Methodology

For each DNA sequence, we iterate across every k-mer and report those that conform to the provided IUPAC definition for transcription factor binding sites. For each identified binding site (whether it is shared between both sequences or not), we report the sequence that exists at the position of the binding site for both sequences. 
The specificity of each binding site depends on whether it exists in one sequence or both sequences. If the binding site exists in both sequences at the same position, then it is considered shared. If the binding site exists in one sequence but not the other, report only the name of the DNA sequence that it exists in. 


## Parameters

<span style="color: red;">*</span> indicates required parameter

### Input and Outputs

- <span style="color: red;">*</span>**Relative Affinity PBM Data (.tsv)**
    - This file is the normalized PBM data file for a transcription factor obtained from `defineTfSites.` It contains the relative affinity for every possible k-mer.
- <span style="color: red;">*</span>**Binding Site Comparison Table (.tsv)**
    - Name of the output file containing a list of all binding sites in both sequences and their specificity.

### Other Parameters

- <span style="color: red;">*</span>**TF Name (string)**
    - Name of transcription factor to analyze.
- <span style="color: red;">*</span>**TF IUPAC Definition (string)**
    - IUPAC definition of core transcription factor binding site (see [here](https://www.bioinformatics.org/sms/iupac.html)).
- <span style="color: red;">*</span>**Name of Sequence 1 (string)**
    - Name of the first DNA sequence.
- <span style="color: red;">*</span>**Sequence 1 (string)**
    - First DNA sequence.
- <span style="color: red;">*</span>**Name of Sequence 2 (string)**
    - Name of the second DNA sequence.
- <span style="color: red;">*</span>**Sequence 2 (string)**
    - Second DNA sequence.



## Input Files
 
1.  Relative Affinity PBM Data (.tsv)
    - Columns
        - `Seq:` the sequence of every possible k-mer
        - `Rel_aff:` the relative affinity of the k-mer normalized to the max IUPAC k-mer

```
seq             rel_aff
AAAAAAAA        0.147
AAAAAAAC        0.107
AAAAAAAG        0.13
AAAAAAAT        0.125
AAAAAACA        0.123
```

```
seq             rel_aff
AAAAAAAA        0.085
TTTTTTTT        0.085
AAAAAAAC        0.061
GTTTTTTT        0.061
AAAAAAAG        0.057
```
       
## Output Files

2.  Binding Site Comparison Table (.tsv)
    - Columns
        - `Align_pos_1idx:` Position of the binding site (1-indexed, 1 is the first column)
        - `Site_direction:` direction of the binding site (+ if it follows the given IUPAC or - if it follows the reverse complement of the IUPAC)
        - `Specificity:` The name of the sequence that the binding site belongs to, or “shared” if both sequences contain the binding site
        - `Seq_[Name of Sequence 1]:` The sequence that exists at align_pos_1idx of sequence 1
        - `Seq_[Name of Sequence 2]:` The sequence that exists at align_pos_1idx of sequence 2
        - `Aff_[Name of Sequence 1]:` The affinity of the k-mer sequence, if it is a binding site. Otherwise none is reported.
        - `Aff_[Name of Sequence 2]:` The affinity of the k-mer sequence, if it is a binding site. Otherwise none is reported.
        - `Tf_name:` The name of the transcription factor whose binding site is identified.. 

```

align-pos-1idx	 site-direction	  specificity	  seq-chick	seq-human	aff-chick	aff-human	tf-name
231              -	          chick	          TTATCCTC		        0.266		                 ets
238              -	          human		                TCATCCAT		        0.06	         ets
97               +	          shared          ATGGAAAA      TTGGAAAA	0.071	        0.056	         ets
188              -	          shared          ACTTCCAT      ACTTCCAT	0.059	        0.059	         ets
51               -	          shared          CTTTCCAA      CTTTCCAA	0.05	        0.05	         ets
230              -	          chick	          TTTATCCT		                        0.138            gata

```
    
  
## Example Data

[Example input data is available on github](https://github.com/genepattern/tfsites.CompareEnhancers/data)
    
## References

    
## Version Comments

- **1.0.0** (2023-12-06): Initial draft of document scaffold.
- **1.0.1** (2024-02-02): Draft completed.
