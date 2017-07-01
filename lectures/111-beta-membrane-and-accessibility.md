More Globular - More Likely Expressed















1.11 Beta Membrane and Accessibility

###### 22.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170620_tmb_acc.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=88jQ5H3orzc&index=10&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J)

---

#### Beta Barrels

TMB = Trans Membrane Barrel

* "barrels" formed out of β-sheets connected by hydrogen bonds,which go through the membrane
* looking from the tops they have a hole
* they are pores, letting anything pass that is small enough

##### Beta Barrel Prediction: PROFtmb

###### Model Design**:**

* Hidden Markov Model
* structure based labels \(states\)
  * inside loop
  * outside loop
  * strand up
  * strand down

_How to assess whether this model makes sense?_

* Count the different states in the set of proteins, where you know \(from experiments where the barrels are\)
* Put the observation into the **priors** for the **HMM **\(Hidden Markov Model\) and train for all the others
* Check the results \(per residue\) predicted vs observed

**Conclusion**: Remarkable performance

###### BUT: Can we distiguish proteins with / without TMB?

**Challenges:**

* Where do barrel domains start / end?
* Sometimes barrels are built out of several peptide chains \(proteins\)
* Per Protein Performance: **Accuracy vs Coverage**
  * Where to put the threshold when analysing a new protein?
    * Intuitive / Literature: **Intersection of Accuracy and Coverage**
    * Optimized per Case: E.g. for Master Thesis high accuracy if more important than coverage, as experimental biologists will follow up on only a few of the found proteins in further research

#### 

#### Accessibility

What is it about? Why is this relevant?

* accessibility of residues to water ❓
* outside vs inside❓

**1\) Absolute Accessibility**: ASA \(square Ångstrøm, 1 Å = 0.1 nm\)

**Long side chains may appear more accessible**: _Different amino acids have a different length of their side chain and thus the absolute accessibility per amino acid differs._

Using absolute accessibility may lead to wrong conclusions.

**2\) Relative Accessibility: **ASA / max ASA

**3\) "States":**

* buried, exposed
* buried, intermediate, exposed

> Note: It doesn't matter whether something is 80% or 100% exposed, but it does matter whether something is 0% or 20% exposed. Also, drawing the line where to set the "best" threshold between the states is discussed in academia.
>
> RostLab Approach: Square Root -&gt; Switch from percentage to predicting 10 states

#### Solvent Accessibility

Accessibility helps in predicting protein function.

* sub cellular localization
* protein-protein interactions
* flexibility / motion from structure

**Historically: **Prediction by hydrophobicity

* hydrophobic: inside
* hydrophilic: outside

**PHDacc: **Machine Learning Approach

* 10 output units
* Advantage: No need to decide on treshold beforehand. Threshold can be chosen for future needs.
* Advantage: Mapped to a 2 state system \(burried / exposed\) each prediction also carries the confidence in the prediction

**Detailed Prediction Problematic: ❓**

**ConSurf: **Significant gain by evolutionary information \(in/out with &gt; 75% accuracy\)

