## 1.4 Alignments 2

###### 16.05.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170516_alignments2.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=B-40K3FFSKo&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=4)

---

#### 1. Recap

**3D Comparison:** There is a way to look at proteins in 3 dimensions

* 1D -  secondary structure prediction
* 2D - distance map
* 3D - real 3D coordinates

**Dynamic Programming**

* **Global** \(Needleman-Wunsch\) or **Local** \(Smith-Waterman\)
* With or without **Gaps**
  * Linear Gap Penalty: Opening and extending a gap have the same cost
  * Affine Gap Penalty: Opening a new gap is more expensive than extending an existing one
* **Scoring Matrices**
  * For each pair of residues you can read off, how much you gain by aligning these 2 residues

**BLAST:** _Basic Local Alignment Search Tool_

* Dynamic Programming is slow for large scale comparisons
* Speed search up by hashing words \(seed = 3 amino acids / residues\)
* After matching a word, try to extend the match by dynamic programming
* **Major Challenge:** Get the statistics right
  * _How significant is a match_ against the background probability entire database

**Question:** What is the major challenge of BLAST?

> Getting the statistics right: BLAST needs to know, h_ow significant a match is_, by comparing it against the background probability of the entire database.

#### 2. Pairwise Alignment Accuracy

**PSI:** Percentage Sequence Identity

**Zones:**

* **Daylight-Zone:** PSI, where it can be assumed that from a similar sequence follows similar structure
* **Twilight-Zone:** PSI, where it is not possible to infer similar structure from similar sequence \(the signal fades\)
* **Midnight-Zone:** PSI, where sequence similarity does not tell anything about structure similarity \(down to random changes\)

```markdown
# Note: The Midnight-Zone is, where most proteins of similar structure sit
```



**Question:** Why is it interesting to find similar proteins out of the Twilight / Midnight Zone?

> The Midnight-Zone is, where most proteins of similar structure sit.

**Question:** Why is it that even with only 40% PSI, we can still assume similar structure? Could we randomly change 60% of the residues in the lab and get a new protein with similar structure?

> * These 60% of changed residues happened under evolutionary pressure and are not random
>   * mutations that did not change structure & function survived \(we can observe them today\)
>   * mutations that did change structure & function most likely did not survive
> * Thus randomly changing 60% of residues in a proteins, would not result in a similar protein

#### 3. Multiple Sequence Alignment

#### 4. Profiles

#### 5. PSI-BLAST

**PSI-BLAST: **_Position-Specific Iterative Basic Local Alignment Tool_

#### 6. Hidden Markov Models \(HMM\)

#### 7. HMM for Alignment

#### 8. Genetic Algorithm for alignment

#### 9. Profile-Profile Aligments



