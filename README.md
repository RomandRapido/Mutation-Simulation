# SA2-Statistical-Computing
Romand Lansangan, Jinghua Yang, and Zion Ramilo

Protein-based therapeutics constitute an important class of drugs used for the treatment of multiple diseases, including cancers, genetic disorders, autoimmune diseases, and infectious diseases. Based on Singh and Tripathi (2023), the global market and demand for therapeutic proteins are increasing rapidly, but the manufacturing and production of protein-based therapeutics are highly complex processes. Singh and Tripathi (2023) have attributed the critical challenge that protein-based therapeutics have to the poor membrane permeability, poor in vivo stability, and short half-life. 

These limitations stem largely from the intrinsic sensitivity of proteins to environmental conditions such as temperature, pH, and enzymatic degradation. In particular, elevated or fluctuating temperatures can lead to misfolding, aggregation, or denaturation, ultimately reducing drug efficacy and shelf life.

One strategy to enhance protein stability involves introducing mutations that improve folding or structural resilience. However, these mutations can also introduce unpredictable effects on protein stability, especially in the context of temperature, where even single-point changes may either stabilize or destabilize the protein's folded state, thus reducing drug efficacy and shelf life.

Moreover, based on a study of Kontopoulos, Patmanidis, Barraclough, and Pawar (2020), there exists no theoretical basis for the relationship, possibly because it is extremely challenging to experimentally quantify the effects of all possible nonsynonymous mutations for a given protein at multiple temperatures. 

Studies report temperature rises have made mutations increasingly deleterious  (Guo et al., 1996; Dieterle et al., 2010; Ndo et al., 2018 as cited in Kontopoulos et al., 2020), which is typically hypothesized to be due to the decline in protein stability at elevated temperatures (Puurtinen et al., 2016 as cited in Kontopoulos et al., 2020; Berger et al, 2020). Under this view, ΔΔG is assumed to be constant and independent of temperature, where it is known as the temperature-invariant ΔΔG hypothesis.

Our study shall challenge this assumption, using empirical data of Dehouck et al. (2011) which has a diverse set of proteins to investigate whether mutation-induced changes in protein stability (ΔΔG) vary with temperature. With our project, we aim to test the validity of the temperature-invariant ΔΔG hypothesis and explore the possibility of the effect of mutations on protein stability being temperature-dependent.

Given the known thermodynamic sensitivity of proteins, that mutations may become more destabilizing at higher temperatures, there is a critical need to reassess this assumption. This study addresses this gap by statistically modeling ΔΔG as a function of temperature across a diverse dataset of protein mutations, aiming to reveal whether mutation effects on protein stability are indeed temperature-dependent.
---
Links:
[Bootstrap & Jacknife](https://colab.research.google.com/drive/1_lU8wqN5WjTKGDeIJ1uQctmn9EhdbO3X?usp=sharing)

[Probability Density Estimate](https://colab.research.google.com/drive/1csVdBVHHj1WSCnt__5frlS9Ay43HLn0K#scrollTo=y74F9ZZa3z6j)
---
References:

Berger, D., Stångberg, J., Baur, J., & Walters, R. J. (2020). Elevated temperature increases genome-wide selection on de novo mutations. bioRxiv. https://doi.org/10.1101/2020.10.13.337972

Dehouck, Y., Kwasigroch, J. M., Gilis, D., & Rooman, M. (2011). PoPMuSiC 2.1: a web server for the estimation of protein stability changes upon mutation and sequence optimality. BMC bioinformatics, 12, 151. https://doi.org/10.1186/1471-2105-12-151

Dieterle, M. G., Wiest, A. E., Plamann, M., & McCluskey, K. (2010). Characterization of the temperature-sensitive mutations un-7 and png-1 in Neurospora crassa. PLoS ONE, 5(5), e10703. https://doi.org/10.1371/journal.pone.0010703

Guo, Q., Penman, M., Trigatti, B. L., & Krieger, M. (1996). A single point mutation in e-COP results in temperature-sensitive, lethal defects in membrane transport in a Chinese hamster ovary cell mutant. Journal of Biological Chemistry, 271(19), 11191–11196. https://doi.org/10.1074/jbc.271.19.11191

Kontopoulos, D.-G., Patmanidis, I., Barraclough, T. G., & Pawar, S. (2020). Higher temperatures worsen the effects of mutations on protein stability. bioRxiv. https://doi.org/10.1101/2020.10.13.337972

Singh, D. B., & Tripathi, T. (2023). Protein-based therapeutics (1st ed.). Springer Singapore. https://doi.org/10.1007/978-981-19-8249-1


