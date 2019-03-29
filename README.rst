RU-Spring-2018L Molecular View of Human Anatomy: Molecular Mechanisms of Antibiotics Action and Resistance and the Comprehensive Antibiotic Resistance Database
--------------------------------------------
 
The `Comprehensive Antibiotic Resistance Database <http://card.mcmaster.ca>`_ (CARD) is a bioinformatics resource for antimicrobial resistance genes, their products and associated phenotypes. With a focus on the molecular determinants of AMR, CARD is heavily used for molecular surveillance of AMR in the environment, agriculture, and clinic:

.. image:: card_overview.jpg

**CARD reference sequences and significance cut-offs are under constant curation - as CARD curation evolves, the results of RGI evolve.**

Lab Goals
--------------------------------------------

The goals of this laboratory is to introduce students to the diversity of molecular mechanisms underlying AMR, provide a practical exposure of databases and biocuration, illustrate the power of ontologies for organizing complex biomedical information, and provide practical skills in annotation of clinical genome sequences. All analyses will be performed online at http://card.mcmaster.ca

Antibiotic Resistance Ontology
--------------------------------------------

At the heart of the Comprehensive Antibiotic Resistance Database is the Antibiotic Resistance Ontology (ARO), a controlled vocabulary for organizing and cross-linking diverse data within CARD.

**Question #1. Browsing from the CARD home page, what are the seven major branches of the ARO?**

**Question #2. How many major drug classes are represented in the ARO? These are tagged as [Drug Class] within the ARO.**

**Question #3. Using the search box, find the ARO term for the MCR-1 protein. Outline what drugs MCR-1 confers resistance to and via which mechanism. Explain the mechanism by exploring the ARO terms associated with MCR-1.**

Detection Models & the Resistance Gene Identifier
--------------------------------------------

Continuing to look at CARD’s entry for MCR-1, you’ll see that ARO terms describing specific genes include curated Detection Models, which define the parameter and sequence space needed to predict presence of AMR genes in raw genome or metagenome samples. CARD’s collection of Detection Models are used by the `Resistance Gene Identifier <https://card.mcmaster.ca/analyze/rgi>`_ software (RGI) to annotate genomes, with all results categorized using terms in the ARO.

**Question #4. Again using the search box, contrast MCR-1 and Mycobacterium tuberculosis embB mutations conferring resistance to ethambutol. How does the mechanism of resistance differ between these two genes? What extra information is required in the embB detection model?**

If DNA sequences are submitted, RGI first predicts complete open reading frames (ORFs) using `Prodigal <https://github.com/hyattpd/Prodigal>`_ (ignoring those less than 30 bp) and analyzes the predicted protein sequences. Short contigs, small plasmids, low quality assemblies, or merged metagenomic reads should be analyzed using Prodigal's algorithms for low quality/coverage assemblies (i.e. contigs <20,000 bp) and inclusion of partial gene prediction. If the low sequence quality option is selected, RGI uses Prodigal anonymous mode for open reading frame prediction, supporting calls of partial AMR genes from short or low quality contigs.

The RGI currently supports CARD's `protein homolog models <https://card.mcmaster.ca/ontology/40292>`_ (use of BLASTP or `DIAMOND <https://ab.inf.uni-tuebingen.de/software/diamond>`_ bitscore cut-offs to detect functional homologs of AMR genes), `protein variant models <https://card.mcmaster.ca/ontology/40293>`_ (for accurate differentiation between susceptible intrinsic genes and intrinsic genes that have acquired mutations conferring AMR, based on CARD's curated SNP matrices), `rRNA mutation models <https://card.mcmaster.ca/ontology/40295>`_ (for detection of drug resistant rRNA target sequences), and `protein over-expression models <https://card.mcmaster.ca/ontology/41091>`_ (which detect efflux subunits associated AMR, but also highlights mutations conferring over-expression when present).

+----------------------------------------------------------+---------------------------------------------------+
|    Example                                               | AMR Gene                                          |
+==========================================================+===================================================+
|    Protein Homolog Model                                 | `NDM-1 <https://card.mcmaster.ca/ontology/36728>`_| 
+----------------------------------------------------------+---------------------------------------------------+
|    Protein Variant Model                                 | `Acinetobacter baumannii gyrA conferring          |
|                                                          | resistance to fluoroquinolones                    |
|                                                          | <https://card.mcmaster.ca/ontology/40507>`_       |
+----------------------------------------------------------+---------------------------------------------------+
|    rRNA Mutation Model                                   | `Campylobacter jejuni 23S rRNA with mutation      |
|                                                          | conferring resistance to erythromycin             |
|                                                          | <https://card.mcmaster.ca/ontology/42445>`_       |
+----------------------------------------------------------+---------------------------------------------------+
|    Protein Over-Expression Model                         | `MexR <https://card.mcmaster.ca/ontology/36645>`_ | 
+----------------------------------------------------------+---------------------------------------------------+

The RGI analyzes genome or proteome sequences under three paradigms: **Perfect**, **Strict**, and **Loose** (a.k.a. Discovery). The Perfect algorithm is most often applied to clinical surveillance as it detects perfect matches to the curated reference sequences and mutations in the CARD. In contrast, the Strict algorithm detects previously unknown variants of known AMR genes, including secondary screen for key mutations, using detection models with CARD's curated similarity cut-offs to ensure the detected variant is likely a functional AMR gene. The Loose algorithm works outside of the detection model cut-offs to provide detection of new, emergent threats and more distant homologs of AMR genes, but will also catalog homologous sequences and spurious partial hits that may not have a role in AMR. Combined with phenotypic screening, the Loose algorithm allows researchers to hone in on new AMR genes. All results are organized via the `Antibiotic Resistance Ontology <https://card.mcmaster.ca/ontology/36006>`_ classification: AMR Gene Family, Drug Class, and Resistance Mechanism. **Note**: All Loose hits of 95% identity or better are automatically listed as Strict.

Link: `Resistance Gene Identifier <https://card.mcmaster.ca/analyze/rgi>`_

**Question #5. Using the Resistance Gene Identifier software, analyze plasmid HQ451074.1 using only Perfect and Strict hits. Trying the RGI visualizations and table view, which are all based on the ARO, which resistance genes or variants exist in this plasmid sequence, which drugs classes do they confer resistance to, and via which mechanisms?**

**Question #6. Using the Resistance Gene Identifier software, analyze genome AE014613.1 from Salmonella enterica using only Perfect and Strict hits. Which mutation-based antimicrobial resistance is present in this genome, i.e. which genes and effected drugs? Are any of these detected mutations from the same pathogen? Do you think this pathogen will be resistant to these drugs?**

Super Bugs
--------------------------------------------

We have only two drug classes of ‘last resort’, which we only use in extreme circumstances. These are colistin and fourth-generation carbapenems. In that last 10 years, two genes have emerged that cause resistance to these drugs: MCR proteins against colistin, NDM proteins against fourth-generation carbapenems.

Link: `Resistomes & Variants <https://card.mcmaster.ca/genomes>`_

**Question #7. CARD routinely analyzes the thousands of genomes, plasmids, and whole genome shotgun assemblies available in GenBank. Using CARD’s Resistomes & Variants section, can you find a pathogen with both of these genes? Which pathogen contains these genes and how many drug classes can it resist? Would you consider this a super bug?**

Clinical Samples
--------------------------------------------

At McMaster University and in association with our regional hospitals, we have a AMR surveillance program where any infection reported resistant to 3 or more drugs is isolated, cultured, screened for resistance to a panel of 18 antibiotics, has its genome sequenced, and full resistome predicted by the RGI. We are sharing data from two of these isolates to you as a challenge to predict the mechanisms of resistance.

**Question #8. Sample 1 has been identified as a vancomycin resistant Enterococcus, but the exact species identification is uncertain. Using the RGI using Perfect & Strict, explain the underlying mechanism for the observed vancomycin resistance. What is the genetic underpinning for this mechanism?**

Sample 2 has proven to be a difficult analysis that illustrates the limits of sequence-based analysis. Specifically, it has strong aminoglycoside resistance and we suspect RGI is under-predicting aminoglycoside resistance genes. Explore the RGI results for this gene using Perfect, Strict, and Loose. 

**Question #9. Which aminoglycoside genes are predicted as Perfect or Strict?**

Link: `PDB Sequence Search tool <http://www.rcsb.org/pages/search_features#search_sequences>`_

**Question #10. The CARD website cannot visualize all of the Loose hits, but if you sort the Table View by “ARO Term” you will see three Loose hits to AAC(6') genes. Use the “Download All” button and open the “*.txt” file in EXCEL to find the “Predicted_Protein” sequences for these three entries. Use the PDB Sequence Search tool to analyze these sequences against known structures. Do you think any of these three genes are functional AAC(6') genes? If so, why do you think these sequences are in not in CARD?**

Clinical Resistance Challenge
--------------------------------------------

One of our local hospitals has a history of Clostridium difficile infections and we have performed whole-genome sequencing surveillance of both carrier (i.e. colonized, but no symptoms) and symptomatic patients. Normally, C. difficile is quite responsive to antibiotics, but we have recently seen resistance to gentamicin and acriflavin. Isolate genome sequencing is provided for a small number of resistant and sensitive isolates. Use the `Resistance Gene Identifier <https://card.mcmaster.ca/analyze/rgi>`_ to analyze the resistomes of these isolates.

**Question 11. Can you explain the resistance to gentamicin and acriflavin? If so, which genes and resistance mechanisms are responsible? Do you see evidence that the resistance is plasmid-borne and thus a threat for tranmission of AMR?**

**Question 12. Fidaxomicin, a macrolide antibiotic, was recently approved for treatment of C. difficile infections. Do you predict any resistance to this antibiotic?**

Curation Challenge
--------------------------------------------

Vancomycin is the preferred front-line treatment for C. difficile infection, with low levels of resistance. Yet, our CARD:Shark text mining algorithms recently detected a paper describing a novel mechanism of vancomycin resistance: Leeds JA, et al. 2014. J. Antimicrob. Chemother. 69(1):41-4 In vitro selection, via serial passage, of Clostridium difficile mutants with reduced susceptibility to fidaxomicin or vancomycin. `PMID 23887866 <https://www.ncbi.nlm.nih.gov/pubmed/23887866>`_

**Question #12. Review this paper and decide how the resistance would be added to CARD, specifically what type of Detection Model and where it would connect to the Antibiotic Resistance Ontology.**

