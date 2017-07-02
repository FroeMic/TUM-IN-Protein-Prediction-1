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



