# rgenexcom (RNA-seq Gene Expression Comorbidities)
Web application for the manuscript <a href="https://doi.org/10.1101/2021.07.22.21260979"><br>Patient stratification reveals the molecular basis of disease comorbidities</br></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary><h2 style="display: inline-block">Table of Contents</h2></summary>
  <ol>
    <li>
      <a href="#web-application">Web Application</a>
    </li>
    <li>
      <a href="#paper">Paper</a>
    </li>
    <li><a href="#documentarion">Documentation</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
Web application: <a href="http://disease-perception.bsc.es/rgenexcom/">http://disease-perception.bsc.es/rgenexcom/</a>

rgenexcom is a web application that allows for both detailed studies on the molecular mechanisms underlying specific comorbidities and large-scale studies on the molecular basis of comorbidities. 


## Paper

The manuscript is already available in MedRxiv [https://doi.org/10.1101/2021.07.22.21260979](https://doi.org/10.1101/2021.07.22.21260979 )

### Abstract
Epidemiological evidence shows that some diseases tend to co-occur; more exactly, certain groups of patients with a given disease are at a higher risk of developing a specific secondary condition. Despite the considerable interest, only a small number of connections between comorbidities and molecular processes have been identified.
Here we develop a new approach to generate a disease network that uses the accumulating RNA-seq data on human diseases to significantly match a large number of known comorbidities, providing plausible biological models for such co-occurrences. Furthermore, 64% of the known disease pairs can be explained by analysing groups of patients with similar expression profiles, highlighting the importance of patient stratification in the study of comorbidities.
These results solidly support the existence of molecular mechanisms behind many of the known comorbidities. All the information can be explored on a large scale and in detail at <a href="http://disease-perception.bsc.es/rgenexcom/">http://disease-perception.bsc.es/rgenexcom/</a>. 

### Description of the web application
To facilitate the visualization and exploration of the generated networks, we implemented a web application that displays the Disease Similarity Network (DSN) and the Stratified Similarity Network (SSN) in a dynamic manner (Chang et al., 2016). The user can filter the networks by the type of interactions (positive or negative) and by selecting a minimum and maximum threshold for the edge’s weight. Community detection algorithms (greedy modularity optimization (Pons and Latapy, 2006) or random walks (Clauset et al., 2004) can be applied to the filtered network and interactions involving specific nodes can be filtered and highlighted. Furthermore, the molecular mechanisms behind diseases and disease interactions can be easily inspected and compared. 


## Documentation

### Disease Similarity Network (DSN)

First, we implemented an RNA-seq pipeline to perform Differential Expression Analysis for each disease. Next, we computed the spearmans' correlation between the diseases' gene expression profiles. We kept significant interactions after multiple testing correction (FDR < 0.05).

The obtained DSN contains positive and negative interactions, representing diseases with significantly similar and dissimilar gene expression profiles, respectively. Next, we evaluated the overlap of the positive interactions in the DSN with the epidemiological network from Hidalgo et al. Positive interactions in the DSN described in this epidemiological network are represented with red dashed lines.


### Stratified Similarity Network (SSN)

We stratified each disease into subgroups of patients with similar expression profiles (meta-patients) by applying the k-medoids clustering algorithm to its normalized and batch effect corrected gene expression matrix. Next, we performed Differential Expression Analyses for each meta-patient.

To analyze the disease subtype-associated comorbidities, we built the Stratified Similarity Network (SSN) connecting meta-patients and diseases based on the similarities of their gene expression profiles (following the same methodology described for the DSN). The resulting Stratified Similarity Network (SSN) contains three types of interactions: (1) the previously described disease-disease interactions, (2) interactions connecting different meta-patients and (3) interactions connecting meta-patients to diseases.


### Molecular mechanism behind diseases

It shows the Reactome pathways significantly dysregulated in human diseases by pathway category. For each disease, Reactome pathways significantly over and underexpressed were identified using the GSEA method (FDR <= 0.05). Ward2 algorithm was applied to cluster diseases based on the Euclidean distance of their binarized Normalized Effect Size (1s, and -1s for over and underxpressed pathways). The heatmap shows the dysregulated Reactome pathways (rows) in the diseases (columns), where over and underexpressed pathways are blue and red colored respectively.


### Molecular mechanism behind disease interactions

Over and underexpressed pathways behind epidemiological and not epidemiological interactions for each disease category pair. Percentage of epidemiological versus non epidemiological interactions that share overexpressed or underexpressed pathways. Each point represents a Reactome pathway category. The size of the points corresponds to the mean number of shared pathways in the epidemiological interactions. The color corresponds to the ratio of the mean number of shared pathways in epidemiological versus non epidemiological interactions.


### Get genes and pathways

In this section you can access the differentially expressed genes and pathways in a given phenotype (disease or meta-patient) and commonly dysregulated in phenotype pairs or groups.

If you select one phenotype, you will get the table of dysregulated genes and pathways for that phenotype. You can filter the tables by selecting only the features that are significantly altered or by selecting only the over or underexpressed features.
If you only select two or more phenotypes, you will get the genes or pathways that are significantly altered in all those phenotypes. Again, you can select only the over or the underexpressed features.



