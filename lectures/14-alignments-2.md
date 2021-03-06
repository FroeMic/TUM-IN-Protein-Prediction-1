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

**Going deeper into the Twilight-Zone, the following results are to be expected:**

1. True Positives go up in absolute numbers
2. False positive increase \(drastically\) in absolute numbers

##### 2.1 HSSP Curve

**HSSP:** Homology-derived Secondary Structure of Proteins

###### How to get the curve?

1. Get all 3D structures from PDB 
2. Remove bias \(sequence unique subset\)
3. And compare 'all vs redundancy reduced set'
   1. compare 3D structure \(e.g. RSMD\)
   2. compare sequence

###### Result: Sequence Conservation of protein structur

![](/assets/Screen Shot 2017-07-03 at 09.08.35.png)🕵🏻 **Observations**

* Over the curve \(daylight-zone\), many true-positives \(sequence identity -&gt; similar 3D structure\)
* Under the curve \(upon entering the twilight zone\)
  * Explosion of **false positives**
  * but also **significant increase **\(x10\) of **true positives** \(This is why we want to go into the Twilight Zone!!\)

**Question:** Why is it interesting to find similar proteins out of the Twilight / Midnight Zone?

> The Midnight-Zone is, where most proteins of similar structure sit.

**Question:** Why is it that even with only 40% PSI, we can still assume similar structure? Could we randomly change 60% of the residues in the lab and get a new protein with similar structure?

> * These 60% of changed residues happened under evolutionary pressure and are not random
>   * mutations that did not change structure & function survived \(we can observe them today\)
>   * mutations that did change structure & function most likely did not survive
> * Thus randomly changing 60% of residues in a proteins, would not result in a similar protein

**Question:** Why are certain proteins / structure multiple times in the PDB?

> * different resolution of 3D structure
> * different goals of publication produced \(new\) 3D structures
>   * folding sites
>   * binding partners
>   * etc ...

#### 3. Multiple Sequence Alignment

Dynamic Programming cannot be done efficiently with multiple sequences.

##### 3.1 Multiple Alignment Hack 1: Iterative Pairwise Dynamic Programming

###### Progressive 1

1. Align sequences pairwise int consensus sequences
2. Align resulting consensus 

###### Progressive 2

1. Align all sequences pairwise
2. Start with highest matching alignment
3. Iteratively align sequences into consensus sequence

**How to find consensus?** Different methods, e.g. the first, the more meaningful aa, ...

##### 3.2 Multiple Alignment Hack 1: Map to Tree / Pairwise

##### ClustalW/ClustalX

* all against all \(pairs\) by dynamic programming \(varying substitution matrices\)
* build **phylogenetic tree**
* slow, dynamic programming, for experts

#### 4. Profiles

_Profiles profit from relation of 'families'. _

Building up a profile, we can see certain amino acids that are more conserved than others. Computationally we can identify **sequence** **motifs** that describe such a profile as a regular expression.

##### PSSM \(Position Specific Scoring Matrix\)

You could also write a **profile **into a substitution matrix: A matrix of numbers with scores for each residue or nucleotide at each position.

###### Building a PSSM

1. Absolute Frequencies
2. Add pseudo-counts if necessary
3. relative frequency
4. log likelihoods

❓ **Question:** How are profiles built up? How are the normal noted down? Do we have to know a specific algorithm?

> **Build up algorithm:**
>
> * Take all proteins of PSI over a certain threshold ...
> * ❓
>
> **Profile Formats:**
>
> * Regular Expression
> * PSSM \(Position Specific Scoring Matrix\) ❓

**Question:** What is a PSSM \(Position Specific Scoring Matrix\)?

> A matrix of numbers with scores for each residue or nucleotide at each position. Built, e.g. by PSI-BLAST.

#### 5. PSI-BLAST

_Position-Specific Iterative Basic Local Alignment Tool_

##### PSI-BLAST Steps

**1\) Fast Hashing**: Like BLAST, match 'word'  
**2\) Dynamic Programming Extension between matches:** BLAST + Smith-Waterman  
**3\) Compile Statistics:** EVAL - Expectation Values  
**4\) Collect all pairs and build profile  
5\) ... compare sequences \(profile-sequence\) and iterate**

![](/assets/Screen Shot 2017-07-03 at 10.39.37.png)

**Question:** Which steps are involved in building up a profile with PSI-BLAST?

> **1\) Fast Hashing**: Like BLAST, match 'word'  
> **2\) Dynamic Programming Extension between matches:** BLAST + Smith-Waterman  
> **3\) Compile Statistics:** EVAL - Expectation Values  
> **4\) Collect all pairs and build profile  
> 5\) ... compare sequences \(profile-sequence\) and iterate**

**Question:** Why is PSI-BLAST so fast?

> Because it drastically reduces the length of the comparisons with dynamic programming.

#### 6. Hidden Markov Models \(HMM\)

Hidden Markov Model are another method for creating Machine Learning Models. They are a good choice, if the structure of the problem is known beforehand.

* different states
* each state has transition probabilities to the neighboring states / itself

#### 7. HMM for Alignment

**Generic Profile HMM for alignment**

* Captures matches, insertions, deletions
* Transition and emmission probabilities
* gap penalty handled by variation of transition probabilities
* calculation of probability by multiplying path variables

![](/assets/Screen Shot 2017-07-03 at 10.57.05.png)**Entropy in alignment: **Consider the residue at position **i**

* BEFORE any amino acid is aligned, we expect a particular amino acid to have some prior background probability $$P_0$$ with entropy $$H_0$$
* AFTER the alignment we consider the same column with a _posterior probability _$$P_i + priors \rightarrow H_i$$.  
  **We expect **$$H_i = \begin{cases} 0, & if\ conserved \\ H_0, & if\ varied 
   \end{cases}$$

* $$H_i - H_0$$ reflects the "bits\_saved" by the alignment

With small families \(few members, little divergence\) the entropy is dominated by priors \(= the background noise dominates\)

#### 8. Genetic Algorithm for alignment

❗️❗️❗️ **Independence Assumption NOT needed for genetic algorithm**

```markdown
# All algorithms so far assumed *Independence between residues*: 
# What happens at position i is independent of what happens at position i+x.

# The genetic algorithm does not make this indepence assumption!!
```

* The genetic algorithm works on segments
* through mutations it creates new alignments

**T-Coffee:** much slower, requires pre-processing, Genetic algorithm

#### 9. Profile-Profile Alignments

Compare Profiles to go even deeper into the **Twilight- / Midnight-Zone**

![](/assets/Screen Shot 2017-07-03 at 11.19.32.png)

