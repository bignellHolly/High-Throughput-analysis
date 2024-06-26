# High-Throughput-analysis
Conducted data analysis project using high throughput analysis of the RNA sequencing data from a previous study (Xiaohong Zhao, 2019).
The main goal of this study was to define the differences between the transcriptomes of the parental (HBL2) lines and the derived ABT199 resistant lines. 

## Skills: 
R, statistical analysis, High-Throughput analysis, Running Linux based programs, Bash-scripting, GO- analysis, R package: DSEQ2 (differential gene analysis).

## Aims: 
* Attempt to prepare and check the quality of RNAseq data using various computational programs. 
* Compare the expression of the parental vs derived lines:
  * Analyse differential expression. 
  * Enrichment analysis.
* Deliver a formal presentation of results to expert audience.

## Background
<p>It is widely accepted that drug resistance limits the effectiveness of medication. Increasing evidence has suggested that mechanisms of resistance is driven by epigenetic  and transcriptional reprogramming. </p>
<p></p>Emerging evidence reveals that upon drug treatment small populations of cells transform into what is known as a drug tolerant persister state (DTP). This is significant as it facilitates resistance to therapy whilst allowing opportunities for small populations of cells to grow that maintain this resistance after therapy. (Richard J Youle, 2008)</p>

### What is BCL-2? 

<p>BCL-2 is a protein that is transcribed by the BCL-2 gene. The whole family of proteins produced by this gene regulate cell death and apoptosis. The relevance of BCL-2 is that apoptosis has now been a widely accepted tumour-suppression mechanism. Mutations in other genes, such as dysregulation in MYC expression results in cell proliferation. Therefore, overexpression of BCL-2 in combination with genes such as MYC can influence the development of certain lymphomas and other types of cancers. (Richard J Youle, 2008)</p>

### ABT-199

<p>ABT-199 is a selective inhibitor of the BCL-2 protein. This means that it can suppress a specific response in the BCL-2 gene.  This makes it promising in the treatment of cancers such as Mantle Cell Lymphoma. (Matthew S Davids, 2013) However, many patients who initially respond well develop resistance. The mechanism behind gain of resistance is less well understood and therefore the aim for Zhao et al. was to characterise the main contributors to this.  (Xiaohong Zhao, 2019)</p>

<p> Parent line = not resistant to ABT-199 <br>
Derived line = resistant to ABT – 199 </p>

The purpose of the study was to identify differential expression. Once identified we then attempted to identify the genes that were differentially expressed in order to further characterise and understand the mechanism of resistance. 

## Methods

### Linux 
* Checked the quality of the data using FastQC program to generate quality reports of the data.
* Trimgalore – used in association with cutadapt to remove adapters from reads (cleaning the data). 
* Salmon – used to index the transcriptome against a reference genome and quatify the expression of the samples. 

Once the data was prepared, analysis was carried out using Dseq2 and TopGO programs. 

### R
#### Identifying differential Expression.
<p>Dseq was used to analyse the differential expression between the Parent line and Derived line.
Figure 1 shows an MA plot that illustrates the differential expression between Parent vs Derived line – with log fold change plotted on the y axis and mean or normalized counts between the Parent vs derived on the x axis. </p>

* Log fold change is the log ratio of a genes expression value between the parent vs the derived.  
* S, will show the relative expression between the two.  
<p>On this plot in particular any point above the zero-line shows overexpression in the Derived cells and any point below the zero line suggests overexpression in parent line (aka under expression in derived). </p>
<p>From this we can clearly see a difference in expression – no difference would mean that points would centre at the zero lines. This plot exhinits a large spread – clearly see genes that are amplified in parent and genes that are amplified in derived.</p> 

* Each point is a gene – a point is coloured red when it has a p-value < 0.1 
* In this study we used a confidence threshold of 5%  
* There were 5215 points that were statistically significant (under this limit).

#### Identifying the genes that were the most differentially expressed.

After performing our DESeq differential expression analysis we moved on to performing enrichment analysis of our data. We conducted the following tests:

* ElimKS 
* ClassicFisher 
  * These results are the ones that we thought generated a list of the most informative GO terms. 
  * A difference in most of these processes between parent and derived is in line with what we would expect to see from a change in resistance to a drug. 
  * All the p values from this list were extremely small – the difference in these two processes between parent and derived are incredibly significant.
* Ks Test
  
## Biological implications.

<p>Immune system response scored highly in the enrichment analysis. Immune system response refers to any immune system process that functions in the calibrated response of an organism to a potential internal or invasive threat.  Any dysregulation will cause a change in the way the body responds to a threat – internal or external. And a clear difference in this between Parent and Derived pertains to the fact this is their main difference in the transcriptomes. </p>

## Conclusions
* Our results showed good agreement with ZHAO et al.
* TopGO analysis shows significant differential expression in relevant biological processes
* There is a clear difference between parent vs derived.
  * This is evidenced when looking at MA plot
  * The list of differentially expressed genes that are significant  - 5215 below 5% significance threshold
  * The difference found in the biological processes of the most differetially expressed genes.
 
## References
* Matthew S Davids, A. L. (2013). ABT-199: taking dead aim at BCL-2. Cancer Cell, 139-141.
* Richard J Youle, A. S. (2008). The BCL-2 protein family: opposing activities that mediate cell death. Nature reviews. Molecular cell biology., 47-59.
* Xiaohong Zhao, Y. R. (2019). BCL2 Amplicon Loss and Transcriptional Remodeling Drives ABT-199 Resistance in B Cell Lymphoma Models. Cancer Cell, 752-766.








