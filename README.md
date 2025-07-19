# Simulating Biological Mutation Stability: A Statistical and Mathematical Perspective on Genetic Modifications
#### By: Romand Lansangan, Jinghua Yang, and Zion Ramilo

## Introduction/Problem Statement
Protein-based therapeutics constitute an important class of drugs used for the treatment of multiple diseases, including cancers, genetic disorders, autoimmune diseases, and infectious diseases. Based on Singh and Tripathi (2023), the global market and demand for therapeutic proteins are increasing rapidly, but the manufacturing and production of protein-based therapeutics are highly complex processes. Singh and Tripathi (2023) have attributed the critical challenge that protein-based therapeutics have to the poor membrane permeability, poor in vivo stability, and short half-life. 

These limitations stem largely from the intrinsic sensitivity of proteins to environmental conditions such as temperature, pH, and enzymatic degradation. In particular, elevated or fluctuating temperatures can lead to misfolding, aggregation, or denaturation, ultimately reducing drug efficacy and shelf life.

One strategy to enhance protein stability involves introducing mutations that improve folding or structural resilience. However, these mutations can also introduce unpredictable effects on protein stability, especially in the context of temperature, where even single-point changes may either stabilize or destabilize the protein's folded state, thus reducing drug efficacy and shelf life.

Moreover, based on a study of Kontopoulos, Patmanidis, Barraclough, and Pawar (2020), there exists no theoretical basis for the relationship, possibly because it is extremely challenging to experimentally quantify the effects of all possible nonsynonymous mutations for a given protein at multiple temperatures. 

Studies report temperature rises have made mutations increasingly deleterious  (Guo et al., 1996; Dieterle et al., 2010; Ndo et al., 2018 as cited in Kontopoulos et al., 2020), which is typically hypothesized to be due to the decline in protein stability at elevated temperatures (Puurtinen et al., 2016 as cited in Kontopoulos et al., 2020; Berger et al, 2020). Under this view, ΔΔG is assumed to be constant and independent of temperature, where it is known as the temperature-invariant ΔΔG hypothesis.

Our study shall challenge this assumption, using empirical data of Dehouck et al. (2011) which has a diverse set of proteins to investigate whether mutation-induced changes in protein stability (ΔΔG) vary with temperature. With our project, we aim to test the validity of the temperature-invariant ΔΔG hypothesis and explore the possibility of the effect of mutations on protein stability being temperature-dependent.

Given the known thermodynamic sensitivity of proteins, that mutations may become more destabilizing at higher temperatures, there is a critical need to reassess this assumption. This study addresses this gap by statistically modeling ΔΔG as a function of temperature across a diverse dataset of protein mutations, aiming to reveal whether mutation effects on protein stability are indeed temperature-dependent.

## [Probability Density Estimate](https://colab.research.google.com/drive/1csVdBVHHj1WSCnt__5frlS9Ay43HLn0K#scrollTo=y74F9ZZa3z6j)
A quick data exploration through Probability Density Estimate was done to provide a quick visual estimate against the temperature-invariant ΔΔG hypothesis.

**Key Finding: The exploratory analysis provides strong visual evidence against the temperature-invariant ΔΔG hypothesis.**

The PDE reveals that mutation-induced stability changes (ΔΔG) are indeed temperature-dependent:

1. **Temperature-dependent shift in mutation effects**:
    - Low/Medium temperatures ($\leq$ 42°C): Mutations are predominantly stabilizing (median ΔΔG = -0.995 kcal/mol)
    - High temperatures (42-60°C): Mutations shift toward neutral (median ΔΔG = -0.130 kcal/mol)
    - Very High temperatures (>60°C): Mutations remain near-neutral (median ΔΔG = -0.290 kcal/mol)
2. **Clear rightward shift**: the distribution of  ΔΔG shifts from stabilizing region (negative values) towards a more neutral region (zero) as temperature increase. This provides an avenue to confirm that mutations become increasingly destabilizing at elevated temperatures.   
3. **Non-linear relationship**: The effect is not simply linear. This suggests a complex interactions that warrant sophisticated statistical modeling beyond simple linear assumptions.
4. **Reduced variability at high temperatures**: The narrowing of ΔΔG distributions at very high temperatures indicates that extreme conditions constrain the range of mutational effects.

**Implications**: These findings directly challenge the temperature-invariant ΔΔG hypothesis and support the need for temperature-dependent models when designing stable protein therapeutics, particularly for applications involving temperature fluctuations or storage at elevated temperatures.

**Limitations**: The methodologies used are mere estimations and calls further and rigorous statistical analysis before concluding anything.

## [Permutation Test](https://colab.research.google.com/drive/13l3YQftCrxWYNCC8mCXRO4kG2IXwpzKX?usp=sharing)
To address the limitations of the previous section, a permutation test was conducted to test the independence of temperature and mutation-induced stability changes (ΔΔG) to serve as a rigorous statistical validation.

**Key Finding: The Permutation test provides strong statistical evidence against temperature-invariant ΔΔG hypothesis.

The permutation analysis reveals statistically significant temperature-dependence of mutation effects:
1. **Significant positive correlation**:
	- The observed correlation between temperature and ΔΔG is r=0.190
	- This correlation falls far outside null distribution
	- Under 100,000 permutations, the correlation would be virtually impossible if the two variable are indeed independent.
2. **Protein-specific temperature sensitivity**:
	- The proteins were then stratified based on their protein chains to analyze each of their behaviors.
	- Chain A: Strong positive correlation with p-value=0. This implies that mutations of proteins in this chain become more destabilizing with temperature.
	- Chain B: Strong negative correlation with p-value=0.0118. Interesting reverse pattern showed up here.
	- Chain C: Positive correlation with p-value=0.00248.
	- Chain I and X: No significant correlation suggesting protein specific responses to temperature
**Implications**:
The permutation test conducted confirms what the PDE analysis suggested  and validates the idea that there is a valid relationship between the  △△G  and temperature, although moderate. 

**Limitations**:
The protein specific analysis revealed the different proteins react differently with temperature. This suggest a need for a more sophisticated modeling approaches.
## [Bayesian Linear Regression](https://colab.research.google.com/drive/1fyQaSPhiudw_dG-lFn_dJM32gbDDPkNc?usp=sharing)
To address the potential concerns about classical hypothesis testing, the Bayesian approach with "Bayesian Regression Models" was implement.

**Key Finding: Even with skeptical priors, the Bayesian analysis provided a robust evidence against the temperature-invariant**
1. **Significant temperature effect despite restrictive priors**:
    - Prior for slope: Normal(0, 0.1) - strongly centered on zero. This was done to specifically favor the **temperature-invariant ΔΔG hypothesis**. It's like betting against the presence of relationship.
    - Posterior estimate: $\beta_1 = 0.02$ with 95% CI: [0.01, 0.02]. A rather narrow interval implying that the model overcomes initial skeptical prior to find temperature dependence.  
    - The credible interval excludes zero, rejecting the null hypothesis. Even with conservative prior estimate, the analysis pointed out that there is a relationship between the two variables. 
2. **Robust MCMC sampling**:
    - NUTS algorithm with 4 chains, 10,000 iterations each
    - Excellent convergence diagnostics since, All chains converged well (Rhat = 1.00).
    - This implies that the model arrived at the same answers even using 4 independent chains. We can therefore trust the result. 

**Implications**: Even when starting with strong prior belief in temperature independence (tight prior around zero), the data overwhelmingly supports temperature-dependent mutation effects, providing Bayesian confirmation of earlier findings.

**Limitations**: However concrete the results of the previous analysis, there is still a linear relationship  assumption involved. The model doesn't account for potential non-linearities observed in the EDA. 

## [Bootstrap & Jacknife](https://colab.research.google.com/drive/1_lU8wqN5WjTKGDeIJ1uQctmn9EhdbO3X?usp=sharing)
To examine potential non-linearities suggested in the EDA and assess estimator properties, comprehensive bootstrap analysis was performed with temperature stratification.

**Key Finding: Bootstrap confirms temperature dependence while revealing important nuances about data sparsity and non-linear patterns.**
1. Unbiased estimation with stable variance**:
    - Mean bias: - the mean bias of 0.0001 (negligible) showed that bootstrap estimate are virtually identical to sample estimates. 
    - Variance bias: -0.0007 (minimal underestimation).
    - Bootstrap variance aligns with theoretical σ²/n
    - All these simply imply that bootstrap model itself is working.
2. **Temperature-stratified patterns**:
    - \[0,30)°C: ΔΔG $\approx$ -1.2 kcal/mol (stabilizing) - proteins in this group can tolerate mutations.
    - \[50,60)°C: ΔΔG $\approx$ -0.3 kcal/mol (near neutral) - proteins here are more fragile and mutations neither help nor hurt much.
    - \[70,80)°C: ΔΔG $\approx$ -0.2 kcal/mol (95% CI includes zero) - proteins in here may be at their stability limits.
    - A shift from $\sim$ -1.2 kcal/mol to $\sim$ -0.2 kcal/mol showed a clear upward trend that aligned well with insights gathered from Probability Density Estimate section. 
3. **Statistical significance of temperature correlation**:
    - Full dataset: r = 0.190 (p < 0.001)
    - Restricted <80°C: r = 0.204 (still significant). So the result are not just driven by outliers.
    - Logistic regression: OR = 0.975 per °C [95% CI: 0.97, 0.98]
    - These different statistical approaches all point to the same conclusion that strengthens the confidence in temperature dependence. 
4. **LOESS smoothing reveals non-linearity**:
    - Below 50°C, mutations behave predictably.
    - Sharp transition between 50-70°C. This is the critical section where rapid shift in mutation effects occured.
    - Plateau effect at extreme temperatures. 
    - The findings represent a phase (with regard to temperature threshold) transition in protein behaviour.
**Implications:**
The stratified analysis validates the Bayesian linear model's main conclusion but reveals a more complex story: the relationship shows sharp transitions (particularly 50-70°C) and uncertainty increases dramatically above 80°C due to sparse data. This finding explains why simple linear models might be adequate despite underlying complexity.

## [Resampling For Model Validation](https://colab.research.google.com/github/RomandRapido/Mutation-Simulation/blob/main/Resampling_for_Model_Validation.ipynb)
Finally, to determine if the non-linearities observed in the bootstrap analysis could improve predictive performance, ridge regression with polynomial features was compared to simple linear regression.

**Key Finding: Complex models offer no practical improvement, confirming that the temperature effect, while real, explains only a small portion of ΔΔG variance.**

1. **Negligible performance differences**:
    - Linear model CV RMSE: 1.443
    - Ridge model CV RMSE: 1.444
    - Bootstrap confirms nearly identical performance
    - However, $R^2$ values remain low (~0.038) for both models
- **Consistent results across resampling strategies**:
    - 10-fold CV and 200 bootstraps yield similar conclusions
    - Narrow, overlapping RMSE distributions
    - No practical advantage to polynomial terms
- **Model selection implications**:
    - Ridge penalty selection via grid search
    - Optimal $\lambda$ provides minimal improvement
    - Simpler linear model appears sufficient

This analysis reconciles all previous findings: while temperature dependence is statistically robust (shown by permutation, Bayesian, and bootstrap analyses), it accounts for <4% of total variance. The low $R^2$ explains why the EDA showed overlapping distributions and why protein-specific effects dominated in the permutation analysis.

## Synthesis
Together, these analyses form a coherent narrative:
- **Visual evidence** (EDA) suggested temperature dependence
- **Permutation testing** confirmed statistical significance
- **Bayesian analysis** showed robustness to prior assumptions
- **Bootstrap stratification** revealed data limitations and non-linear patterns
- **Model comparison** demonstrated that simple models suffice despite complexity

## Conclusion
The temperature-invariant **ΔΔG hypothesis is definitively rejected across multiple analytical frameworks**. However, temperature explains only a small fraction of mutation effects, with protein-specific factors playing a dominant role. The relationship is statistically significant but practically modest, with important caveats about data sparsity at extreme temperatures.

---
#### References:

Berger, D., Stångberg, J., Baur, J., & Walters, R. J. (2020). Elevated temperature increases genome-wide selection on de novo mutations. bioRxiv. https://doi.org/10.1101/2020.10.13.337972

Dehouck, Y., Kwasigroch, J. M., Gilis, D., & Rooman, M. (2011). PoPMuSiC 2.1: a web server for the estimation of protein stability changes upon mutation and sequence optimality. BMC bioinformatics, 12, 151. https://doi.org/10.1186/1471-2105-12-151

Dieterle, M. G., Wiest, A. E., Plamann, M., & McCluskey, K. (2010). Characterization of the temperature-sensitive mutations un-7 and png-1 in Neurospora crassa. PLoS ONE, 5(5), e10703. https://doi.org/10.1371/journal.pone.0010703

Guo, Q., Penman, M., Trigatti, B. L., & Krieger, M. (1996). A single point mutation in e-COP results in temperature-sensitive, lethal defects in membrane transport in a Chinese hamster ovary cell mutant. Journal of Biological Chemistry, 271(19), 11191–11196. https://doi.org/10.1074/jbc.271.19.11191

Kontopoulos, D.-G., Patmanidis, I., Barraclough, T. G., & Pawar, S. (2020). Higher temperatures worsen the effects of mutations on protein stability. bioRxiv. https://doi.org/10.1101/2020.10.13.337972

Singh, D. B., & Tripathi, T. (2023). Protein-based therapeutics (1st ed.). Springer Singapore. https://doi.org/10.1007/978-981-19-8249-1


