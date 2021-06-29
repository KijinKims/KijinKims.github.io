---
layout: single
title: "Maser thesis project proposal"
categories: Thesis
---

The trend of the way of identifying pathogens in a sample has been pivoted toward next-generation sequencing (NGS)-based analysis. Metagenomic NGS made it feasible to figure out multiple origins of nucleic acid composites extracted from a given specimen simultaneously. In particular, the new technology sheds light on the field of discovery of new viruses.

For the last decade, several virus detection pipelines have been already introduced, overcoming computational and analytical barriers. Since newly evolved viruses are not reported yet to the research community, aligning de novo assembled contigs against viral sequence databases is regarded as a standard method to seek out a non-discovered virus.

Current pipelines complete their missions by outputting contigs, which are potential viral sequences, with their taxon ID and optionally sequencing reads aligned to the contigs. Virologists, however, cannot make a conclusion only with such an *in silico* screening result. They validate the existence of contigs by a less error-prone method such as Sanger sequencing, mostly preceded by a PCR amplification. Their discovery can be accepted only with any experimental validation.

Designing a proper PCR primer pair is critical to amplify wanted sequences but necessitates consideration of some constraints such as primer length, PCR product length, melting temperature, GC content, self-complementary, etc. If such conditions are not well examined hence screening is done with improper primer pairs, truly existing viral sequences can be deemed as false positive. Virologists design primers either by themselves considering a myriad of constraints or with primer design programs to find the suitable sequence region within contigs. This step is quite time-consuming but has not been in the spotlight. To my knowledge, there is no virus discovery pipeline equipped with the functionality to suggest primer sequences for PCR amplification.

With the help of additional information from pipeline results, there can be room for improvements with regard to the primer selection. To secure reliability of predicted primer pairs, we would better to avoid primer sequences with shallow read depth, single nucleotide variation (SNV) or structural variation to enhance primers' sensitivity and also showing homology against host genome and other viral sequences to increase specificity. These information can be given from the output of preceding steps in pipelines.

MRPrimer is a MapReduce-based primer design tool capable of presenting primer pairs satisfying constraints while excluding candidates homologous with off-target sequences from given query sequences. It features parallel and distributed computation based on MapReduce framework and ranking primer pairs by the penalty score originated from Primer3Plus. The tool was used for constituting pre-built primer database for every viral sequence in NCBI RefSeq. [MRPrimerV] Recently, much faster version of MRPrimer, adapted to GPU computation, called GPrimer is released.

My approach will extract candidates only from input contigs, thus following filtering and ranking steps should be done *ad hoc* after contigs are assembled. Fast computation of GPrimer can drastically decrease running time of the steps.

As a master thesis project, I would like to develop a module to design reliable PCR primer pairs to be used for the amplification of potentially existent contigs, which can be easily integrated into the existing pipeline or independently run with a given input. To this end, I will make full use of GPrimer and modify it so that it can consider informative results from pipelines while ranking candidate primers.
