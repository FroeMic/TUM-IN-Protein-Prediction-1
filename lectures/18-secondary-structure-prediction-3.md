## 1.8 Secondary Structure Prediction 3

###### 08.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170601_sec2.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=BmOE3X6Qh98&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=7)

---

#### 1. Recap

**Goal of Structure Prediction:** Predict the 3D structure and function from an input sequence.

**Cell:** The density of a cell is like solid state, but proteins are still surounded by water

**Relation of Proteins:** We can find out about the relation of proteins by comparing their sequence

* direct sequence-sequence comparison only in the daylight-zone
* building up profiles means to 'pick up the implicit evolutionary signal'

**Question:** Which ways of comparing proteins are there? Why do we need

> * Dynamic Programming \(Brute Force\)
> * Hashing \(e.g. BLAST\)

**Question:** Why are fast search algorithms such as BLAST needed?

> Comparing sequences of length $$n$$ residues is in $$O(n^2)$$. For comparing a single pair this is still fine, but comparing one \(newly found\) protein against all known proteins in the PDB \(about 120 000\) is impossible. Thus we need 'shortcuts' such as BLAST to speed up the search.

**Question:** What is the normal approach when you find / analyse a newly found protein?

> ❓  
> 1\) Sequence the new protein \(if not done yet\)  
> 2\) Run BLAST against the PDB  
> 3\) Run Dynamic Programming against the results from BLAST

**Question:** In terms of CPU, is sequence-sequence as fast as sequence-profile?

> ❓

**Question:** How can it be that even with only 40% sequence identity we assume / observe similar structure?

> The changes in sequences we observe are not random, but follow underlying evolutionary rules. Changes, which affected the structure and thus the function of a protein are simply not likely to survive and thus we do not observe them. Changes, which did not influence the structure / function however, did survive.

**Question:** Why is protein sequence changing? Why are we mutating?

> * Replication Errors \(point mutations\)
> * Radiation
> * Viruses

**Question:** How much do any two unrelated typical humans differ on average?

> On average every pair of humans would differ in one amino acid per protein. \(Though, changes cluster\)

**Question:** In a structure to structure network, which additional information could be used to improve the prediction?

> * E.g. redundant information about the sequence, e.g. parts of it.

**Question:** When training a neural network, how do you choose the next training sample from your test set? Why so?

> Randomly, to avoid correlations



