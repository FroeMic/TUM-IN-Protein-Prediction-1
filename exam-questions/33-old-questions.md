## 3.3 Old Questions

> This section contains possible exam questions sourced from students of previous Protein Prediction I lectures.

### 3.3.1 Exam Structure: 2016ST

> We where able to obtain last years exam structure. Let's try to answer all of the concrete questions :-\)

_Part 1 is mandatory, for the rest choose 3 out of 4._

##### **1. Multiple Choice \(5 questions, 10 points\)**

* Secondary Structure
* RMSD - Protein Similarity
* Hydrogen Bonds \(⍺-helix, β-sheets, long/short bonds\)
* 100% sequence identity =&gt; same structure? \(PIDE\)
* Can modern prediction methods correctly predict structure in the midnight zone?
* About "Cryo-Microscope" ❓
* About "X-Rays" ❓

##### 2**. Sequence Alignment \(10 points\)**

* Explain each of the following alignment techniques and provide one method for each

  * Sequence - Sequence
  * Sequence - Profile
  * Profile - Profile

* General scoring BLOSUM62 matrix vs. PSSM

* Why is the sequence information valuable?

* How BLAST speed up pairwise alignments?

* Global vs Local alignment

##### 3**. Sequence Structure \(10 points\)**

* What data is needed to predict the structure with ML?
* Which tools and db you will use?
* How to prepare data for ML
* Which 2-3 features will help to predict?
* Would you apply method to all protein \(query\)?
* Which measure would you use to evaluate your method?

##### 4**. Protein Structure \(10 points\)**

* Why it is important to know 3D structure?
* Why is it so hard to compare 3D structure?
* Most successful ML algorithm for predicting structure, steps
* Method for experimental structure determination. Short explanation. How many structures are experimentally known?

##### 5**. Machine Learning \(10 points\)**

* General definition of Machine Learning
* Cross validation
* What is ‘feature’?
* ETP explain, example
* Name and describe one ML method
* Name and describe "sequence" in context of PP
* Discuss how to predict Protein Structure from amino-acid sequence using ML
* Q2: which is better, how to prove your’s is better, which value you will publish? \(❓What is Q2\)

### 3.3.2 Lecture 1: Introduction Bioinformatics

**Question:**What is common to life?

> DNA, Protein, RNA

**Question:**How many bacteria do we care around?

> About 2 kilos. Humans carry around more bacterial DNA than human DNA.

**Question:**Which elements make up life?

* 65.0 % - O, Oxygen
* 18.6 % - C, Carbon
* 9.7 % - H, Hydrogen
* 3.2 % - N, Nitrogen
* 1.8 % - Ca, Calcium
* 1.0 % - P, Phosphorus

**Question:**What is life? Can you define it?

> There is no holistic definition of life: Descriptive definitions of life are
>
> * Homeostatis \(regulation of internal environment to maintain constant state\)
> * Organization \(Unit: Cells\)
> * Metabolism
> * Growth
> * Adaptation
> * Response to stimuli
> * Reproduction

**Question: **Are viruses life?

> Strictly speaking NO. Viruses on their own cannot replicate and thus are not alive. However, one could say that viruses are alive / represent life once they infected a cell and replicate.

**Question: **What do bacteria have in common?

> Single Cells

**Question: **What are the differences between prokaryotic and eukaryotic cells?

> **Prokaryotic Cells:** mainly found in bacteria and archaea, usually unicellular, no nucleus, no cell organelles  
> **Eukaryotic Cells:** Found in animals and plants, usually multicellular, have nucleus, have cell organelles

**Question:** How can the density of a cell be described?

> The state inside a cell is almost solid. We can think of a cell similar to a Christmas day on Time Square: Everything is densely packed, but there is still movement.

**Question:**What is the smallest building block of life that can replicate?

> cells

**Question:**How many different cells are in a typical human?

> 200

**Question:**What are the parts of the cell called?

> organelles

**Question:**Which part of the cell is called the "powerhouse"?

> mitochondria

**Question:**What part of a plant is involved with photosynthesis?

> chloroplast

**Question:**What is mitosis?

> cell division

**Question:**Who first used the term cell?

> Robert Hooke

**Question:**How many elements are found in amounts larger than trace amounts \(0.01%\) in our bodies?

> 11

**Question:**When communities of living things interact with non living things they are called ... ?

> ecosystem

**Question:**The most common molecule in the human body is ... ?

> Water: H\_2O

**Question:**What do bacteria have in common?

> Single Cells

**Question: **What is a gene?

> A gene is a region of DNA, which contains all information for the creation of an entire RNA strand.

**Question: **What is DNA made out of?

> DNA is a linear polymer out of 4 bases / nucleotides. DNA exists in cells mainly as a two-stranded structure called the double helix. Each of the bases has a complementary base.
>
> * G: Guanine =&gt; Cytosine
> * A: Adenine =&gt; Thymine
> * T: Thymine =&gt; Adenine
> * C: Cytosine =&gt; Guanine

**Question: **What is RNA made out of?

> RNA is a single stranded linear polymer out of 4 bases / nucleotides.
>
> * G: Guanine
> * A: Adenine
> * U: Uracil
> * C: Cytosine

**Question:** Do all organisms use the same amino acids / codons?

> Different organisms use the same amino acids for proteins. However, they differ in their codon usage \(which RNA triplets are translated into which amino acid\).

**Question: **How many proteins does a typical human have?

> Between 20.000 and 25.000 different kinds of proteins.

**Question:** What are functions of proteins?

> * Defense \(e.g. antibodies\)
> * Structure \(e.g. collagen\)
> * Enzymes \(metabolism, catabolism\)
> * Communication / Signaling \(e.g. insulin\)
> * Ligand binding / Transport \(e.g. hemoglobin\)
> * Storage \(e.g. ferritin\)

**Question: **How many residues long are typical proteins?

> Between 35 and 30.000 residues. The median is around 400.

**Question: **Do proteins consist of units?

> Proteins are built up of several domains. Most proteins have more than 2 domains.

**Question: **How many proteins are known?

> About 85 millions sequences are known. However, the 3D structure \(experimentally determined\) of only 120.000 proteins is known.

**Question: **Is this gap \(known sequences vs known 3D structure\) expected to increase?

> Yes, the gap is expected to increase. The amount of new sequences has increased drastically \(far faster than Moore's Law\) in the past. This is expected to continue. Advances in experimentally determining protein 3D structure could only improve marginally, but today experimentally determining the 3D structure of a proteins still costs about 100 000 EUR.

**Question: **How much data is produced by one sequencing machine per day?

> At full capacity about 5 - 10 terabytes of data per day.



