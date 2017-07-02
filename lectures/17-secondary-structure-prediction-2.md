## 1.7 Secondary Structure Prediction 2

###### 01.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170601_sec2.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=RaMUi10-WmM&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=6)

---

#### 1. Recap

**Goal of Structure Prediction:** Predict the 3D structure and function from an input sequence.

**Proteins: **

* are formed by stringing up amino acids in a chain
* amino acids are between 35 to 30.000 residues long
* amino acids form substructures, called domains in order to fold
* in principle: a domain put into solvent \(water\) folds on its own and adopts a unique 3D structure

**Zones: **There are different 'zones' by percentage of sequence identity, in which we can identify similar structures

* **Daylight-Zone** \(100 % - 40%\)
  * Sequence - Sequence Alignment
  * Assumption: sequence similar -&gt; structure similar
* **Twilight-Zone **\(40% - 20%\)
  * Sequence - Profile Alignment
  * more distant relationships
* **Midnight-Zone** \(20% - 0%\)
  * Profile - Profile alignment
  * even more distant relationships

**Global and Local Alignment:**

**Question: **Relate the terms **Local** and **Global alignment** to the terms **Sequence-Sequence** and **Sequence-Profile**.

> Global alignments refers to aligning sequences \(proteins\) from start to end. Local alignments refers to only aligning parts of the sequences \(e.g. 50 residues\).  
> Throughout Sequence-Sequence, Sequence-Profile and Profile-Profile methods both global and local alignment can be used. I practice mostly local alignment is done.

**Comparative Modeling:**

* Idea:
  * Find a similar sequence with known structure in the PDB \(in the daylight-zone\)
  * Try to use the known 3D structure of the similar protein to model the structure of the unknown protein
  * fix physical / chemical errors of the predicted 3D structure and find most plausible 3D structure
* Reliably predicts **over 40 million proteins**
* However, for **most residues comparative modeling cannot be applied**

#### 2. Secondary Structure Prediction

Secondary Structure Prediction happens in 1D, 2D and 3D. The following chapter will mainly be about 1D Secondary Structure Prediction.

**DSSP** \(Define Secondary Structure of Proteins\) algorithm: Has 8 states

* **H** =** **Helix
* **G** = $$3_{10}$$ Helix
* **I**  = Pi Helix
* **E ** = Extended
* **B** = Beta-bridge, single-strand residue
* **S **= bent
* **""** = loop

**Local Sequence determines secondary structure**!

* Certain local sequence always form the same secondary structure \(⍺-helix, β-strand, loop\).
* Others \(penta-peptides\) are found in 2 different state, **dependent on their environment**

**Question:** What would be a simple method to predict secondary structure?

> 1\) Take known structure  
> 2\) Find longest consecutive run of motifs that **ONLY** occur in one of the 3 states: H \(Helix\), E \(Strand\), O \(Other\)  
> 3\) Check unknown sequence against found motifs

**Question**: What was the first secondary structure prediction method?

> Assuming that a **Proline** would break a helix, the occurrences of proline in a sequence was used to predict helices.

##### 1st Generation Secondary Structure Prediction

💡 **Idea:** Build a frequency table over all amino acids, how often they occur in the secondary structure states based on the proteins where the structure is known.  
**Important:** Bias reduction, to make the set table representative for future. Remove all proteins in comparative modeling range.

1. find a unique subset of proteins with known 3D structure \(PDB\)
2. convert 3D to 1D \(secondary structure\) with DSSP

**Question:** Where do we get the secondary structures from?

> From the DSSP, which defines 8 states in total based on H-bond patterns.

##### How can we measure the performance of secondary structure prediction?





