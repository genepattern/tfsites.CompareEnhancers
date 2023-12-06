# tfsites.CompareEnhancers v1

**Author(s):** Joe Solvason  

**Contact:** Joe Solvason (solvason@eng.ucsd.edu)

**Adapted as a GenePattern Module by:** Ted Liefeld (jliefeld@cloud.ucsd.edu)

**Task Type:** Transciption factor analysis

**LSID:**  urn:lsid:genepattern.org:module.analysis:00448


## Introduction

tfsites.CompareEnhancers compares the two seqs and reports the binding site effect on diff seqs


## Functionality

TBD
 
## Methodology

TBD

## Parameters

<span style="color: red;">*</span> indicates required parameter

- **tf names**<span style="color: red;">*</span>
    - List of transcription factor names (comma separated).
- **tf IUPACs**<span style="color: red;">*</span>
    - List of transcription factor IUPACs (comma separated). 
- **tf normalized PBM files**<span style="color: red;">*</span>
    - TF normalized PBM files
- **first DNA sequence**
    - First DNA sequence
- **second DNA sequence**
    - Second DNA sequence.
- **first.sequence.name**
    - Name of the first DNA sequence.
- **second sequence name**
    - Name of the second DNA sequence.
- **output filename**
    - Output file name



## Input Files

1.  tf normalized PBM files.  Raw PBM data in tsv format [ define format and contents in detail ] 
    


## Creating Input Files from User Data

TBD Describe how to get common data formats into the format needed here
       
## Output Files

  1.PBM: <output prefix>.pbm.tsv.  Tab-separated text file TBD.
    e.g. 
```
seq     rel_aff

align-pos-1idx	site-direction	specificity	seq-chick	seq-human	aff-chick	aff-human	tf-name
231	-	chick	TTATCCTC		0.266		ets
238	-	human		TCATCCAT		0.06	ets
97	+	shared	ATGGAAAA	TTGGAAAA	0.071	0.056	ets
188	-	shared	ACTTCCAT	ACTTCCAT	0.059	0.059	ets
51	-	shared	CTTTCCAA	CTTTCCAA	0.05	0.05	ets
230	-	chick	TTTATCCT		0.138		gata

```
    
  
## Example Data

[Example input data is available on github](https://github.com/genepattern/tfsites.defineTfSites/data)
    
## References

    
## Version Comments

- **1.0.0** (2023-12-06): Initial draft of document scaffold.
