* ## 2.4 Alignments

###### 01.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170601_PP1_alignment.pdf) \| [Wiki](https://i12r-studfilesrv.informatik.tu-muenchen.de/sose17/pp4cs1/index.php/Alignments)

---

#### 1. Keywords

##### Pairwise alignments: global, local \(Needlman-Wunsch / Smith-Waterman\)

**Alignment is needed to**

* compare sequences
* find the best possible alignment to callculate distance measure

**Goal:** Find the arrangement of residues that minimizes / maximizes the scoring function  
**Biology:** Try to maximize the overlap between the sequences

**Parameters:**

* Substitution matrix \(for each pair\)
* Gap Penalties \(linear, affine\)
* global, free-shift \(global, but gaps at the start and end of the alignment are not counted\) , local

_Multiple equally scoring alignments are possible._

**Global Alignment:** Needleman-Wunsch

* Full Length Alignment \(comprises both sequences\)
* Makes sense for sequences of nearly equal length


$$
Naive\ Recursive\ Formular:\ S_{m,n} = max \begin{cases} S_{m-1,n-1} + d(m,n)
\\ S_{m-1,n} + Gap
\\ S_{m,n-1} + Gap
 \end{cases}
$$


**Local Alignment:** Smith-Waterman

* Find the best matching subsequence\(s\) between two sequences
* Length differences do not matter
* Sequences may be quite dissimilar


$$
Naive\ Recursive\ Formular:\ S_{m,n} = max \begin{cases} S_{m-1,n-1} + d(m,n)
\\ S_{m-1,n} + Gap
\\ S_{m,n-1} + Gap
\\ 0
 \end{cases}
$$


##### Dynamic programming as solution for cascading recursion, Backtracking

**Dynamic Programming: **\(for examples, look at bottom\)

1. **Setup matrix:**
   1. Template $$t$$ horizontal, Query $$q$$ vertical 
   2. Fill  the $$1^{st}$$ row / column 
      1. Needleman-Wunsch: with increasing gap penalties
      2. Needleman-Wunsch \(with free-shift\): with zeros
      3. Smith-Waterman: with zeros
2. **For each row **$$m_i$$ \(top -&gt; down\)
   1. **For each position **$$m_{i,j}$$ \(left -&gt; right\)
      1. $$s_1 = m_{i-1,j-1} + SubstitutionMatrix(q_i, t_j)$$
      2. $$g_1 = m_{i-1,j} - GapPenalty$$
      3. $$g_2 = m_{i,j-1} - GapPenalty$$
      4. **Enter **$$max(s1,g1,g2)$$ **into the box and remember which score was selected**
3. **Backtrace**
   1. Find the maximum value
      1. Needleman-Wunsch: in the last row
      2. Smith-Waterman: in the matrix
   2. Follow the path back to the origin and note down the aligment
      1. **Diagonal Step:** Match the corresponding residues
      2. **Step up**: Only take the **Query-Value **\(vertical\), add a gap to the template sequence
      3. **Step Left:** Only take the **Template-Value **\(horizontal\), add a gap to the Query sequence

##### Substitution matrix

**What is better:** A short sequence matched perfectly or a long, but only partly matched sequence? We can't tell yet.

Substitution Matrices are **observation derived weight matrices**

* the score reflects the likelihood of an exchange
* depending on the underlying dataset
* thus, choose your matrix according to the proteins of interest
* Several matrices available: **BLOSUM62, PAM250, PAM100, PAM50**

##### Sequence identity, similarity, conservation

\[Source: [http://homepages.ulb.ac.be/~dgonze/TEACHING/stat\_scores.pdf](http://homepages.ulb.ac.be/~dgonze/TEACHING/stat_scores.pdf)\]

**Score:** A number used to asses the biological relevance of a finding. \(Here it describes the quality of the alignment\)


$$
S = \sum_{i=1}^L S_{r_{1,i}, r_{2,i}} \\ with\ respective\ gap\ penalties,\ if\ r_{1,i}\ or\ r_{2,i}\ is\ a\ gap
$$


**Bit-Score:** A log-scaled version of the score

* In context of sequence alignments \(BLAST\), the **bit-score s'** is a normalized score, which lets you **estimate the magnitude of the search space** to find a score greater or equal to the one you got by chance.


$$
  S' = \frac{\lambda S - ln(K)}{ln(2)}\\ \\ \lambda,\ K\ depend\ on\ the\ substitution\ matrix\ and\ gap\ penalties
$$


* If $$S' = 30$$ this would imply that $$2^{30} = 1\ billion$$ random independent pairwise alignments are needed on average to find a similar score by chance

* Size of the search space can be calculate by $$K * sequenceLength * DBEntries$$

**P-Value: **Probability that an event occurs by chance

* The **p-value** associated to a score **S** is the probability to obtain by chance a score **x** at greater or equal to **S.**


$$
  PVal(S) = P(x \ge S): PVal_{S}^{MSP} =  Ke^{-\lambda S} = Ke^{-ln(2)S' + ln(K)} \\= 2^{-S}
$$


**E-Value:** \(Expectation Value\) Correction of the p-value for multiple testing

* he **e-value** associated to a score **S** is the number of distinct alignments, with a score greater or equal **S**, which are expected to occur in a database search by chance.


$$
  E = m*n*Pval = Kmn*e^{-\lambda S} = \frac{m*n}{2^{S'}} \\ with\ n = length\ of\ query\ sequence,\ m\ = length\ of\ database
$$


**PSI:** Percent Sequence Identity \(Percentage of perfectly aligned residues\)

**Similarity:** Percent of residues matched with a positive score in the Substitution Matrix

##### FASTA format \(basic principle\)

???

##### One letter code for amino acids \(you do not have to learn the code, just know what it means\)

Yes. Find a table with abbreviations here[ https://en.wikipedia.org/wiki/Proteinogenic\_amino\_acid](https://en.wikipedia.org/wiki/Proteinogenic_amino_acid#Side_chain_properties)

##### Homology, homologues/homologs

* **Homology**: Assumption of a common ancestor \(in this context\)
  * Sequence-Similarity is used as evidence for homology
  * not direct observable, because of missing fossils
* **Homolog:** A gene inherited by two species from a common ancestor

##### Multiple Sequence Alignments \(MSAs\)

* **Why? **Search strategies are needed to avoid a combinatorial explosion when running one against all alignments
* many different algorithms available
  * Search Tree
  * Combine Pairwise Alignments
  * Profiles

##### Sequence profile, iterative profile creation

* **Idea:** Build a PSSM \(Position Specific Matrix\)
  * = A probability vector for every amino acid at every sequence position
* several sequences needed to build a profile
* therefore, first search the database for similar sequences
* then compile these sequences into profil
* search database with the profile to retrieve more candidates
* rebuild profile 

##### BLAST

* indexing of database for typically **3-aa-word-seeds**
* list of high-scoring words is used to find similar candidates
* word extension to **HSP \(High Scoring Pairs\)**
* Use Local Alignment of the full sequences
* MANY optimization heuristics

##### PSI-BLAST

* Run BLAST
* Use retrieved proteins to build a profile \(PSSM\)
* Use profile \(PSSM\) to query database for more candidates
* Rebuild Profile
* Repeat search for candidates with new profile until convergence or another stop criterion is reached

#### 2. Exercises

##### 2.1 Questions

**Question:** How can you define similarity between two protein sequences?

> Two ways to define similarity are to compute the percentage of residues that were aligned
>
> * and matched on the same amino acid \(PSI, Percent Sequence Identity\)
> * and matched with a positive score in the Substitution Matrix

**Question: **What does "conservation" mean in the context of sequence alignments?

> * Conserved sequences are similar or identical \(sub\)sequences that occur within protein sequences.
> * By compiling homolgues proteins \(a family\) into a profile, it become clear, which subsequences are more conserved and thus more important for the function of the protein family

**Question:** Why are sequence alignments useful?

> * They are useful because the allow use to find the 'best' possible match between two sequences. Only this allows use to
>   * compare their 3D structure
>   * create predictions about their similarity in 3D structure
>   * make assumptions about their evolutionary relatedness

**Question:** What are the main differences in the algorithms of Global and Local alignment? Why does it make sense to not always perform a global alignment.

> * Global alignment methods always align 2 sequences from beginning to end.
> * Local alignment methods only align subsequences.
>
> * For Global alignment to be meaningful, the sequences should have similar length. Since proteins are between 35 and 30000 residues long, it does not make sense to always use global alignment.
>
> * Also when e.g. looking for proteins with a certain domain it does not make sense to use global alignment, since we are explicitly looking for subsequences.

**Question:** Which amino acids can \(with high likelihood\) be substituted for Leucin without having an effect on protein function?

> Methionine \(2\). Isoleucin \(2\), Valine \(2\), Phenylalanine \(0\), because the have a positive score in the BLOSUM62 matrix

**Question:** Which substitution is more probable according to PAM250 and according to BLOSUM62: \[a\] W &lt;&gt; F \[b\] H &lt;&gt; R

> * W \(Tryptophan\) &lt;--&gt; F \(Phenylalanine\)
>   * BLOSUM: 1
>   * PAM250: 0
> * H \(Histidine\) &lt;--&gt; R \(Arginine\)
>   * BLOSUM: 0
>   * PAM250: 2
>
> =&gt; For BLOSUM W &lt;--&gt; F is more likely to be observed  
> =&gt; For PAM250 H &lt;--&gt; R is more likely to be observed

**Question:** What is a multiple sequence alignment?

> A method to align multiple sequences against each others.
>
> * building a consensus sequence and aligning new sequences against it
> * building a search tree
> * building a profile \(like PSI-BLAST\)

**Question:** What kind of sequences are likely to be used for an MSA? In which relationship are they to each other?

> * Most likely, sequences which we assume a evolutionary relationship \(homology\) will be used. Following the homology assumption, we expect sequences with a high PSI to have a similar structure because they have a common ancestor.
> * Building up a profile with them, would then allow us to discover conserved regions and use the profile to find more candidates in the Twilight Zone with Profile-Sequence comparison.

**Question:** Why would you want to align multiple sequences? What kind of information is contained in MSAs but not directly in e.g. all-against-all pairwise alignments?

> Building up a profile with similar sequences, would  allow us to discover conserved regions which developed under evolutionary pressure.
> By compiling such a family of proteins \(we assume that they have a common ancestor -&gt; homology\) into a profile, we can find more candidates in the Twilight Zone with Profile-Sequence comparison.

**Question:** Given your knowledge of the algorithms for pairwise alignments, how could you calculate an MSA? Is that a feasible approach? Why?

> One approach would be to sequentially align sequences against a consensus sequence. This approach, however, comes with problems such as the need for a strategy how to find the consensus for a certain amino acid at a certain position, the fact that the order of alignment might matter, etc.
>
> A better approach is the creation of a PSSM \(position specific scoring matrix\), which contains for each position of the profile the likelihood that a certain amino acid occurs there.

**Question:** You have a sequence which you would like to find in a database. Which search method and which E-value cutoff do you use, \[a\] if you know your sequence is in the database and only want to find that entry \[b\] if you would like to find homologs.

> ?

**Question:** What is the difference between BLAST and PSI-BLAST?

> ?

##### 2.2 Needleman-Wunsch

**Find the best alignment between the sequences “WHAT” and “WHY”, using the Needleman-Wunsch algorithm, with +1 for a match, -1 for a mismatch, and -2 for a gap.**

_**Note:** In each row all value are written in brackets in the following format \(fromDiagonal, FromLeft, FromTop\). The chosen value is entered in the box_

|  |  | W | H | A | T |
| :--- | :--- | :--- | :--- | :--- | :--- |
|  | 0 | -2 | -4 | -6 | -8 |
| **W** | -2 | 1 \(**1**, -4, -4\) | -1 \(-3, **-1**, -6\) | -3 \(-5, **-3**, -8\) | -5 \(-7, **-5**, -10\) |
| **H** | -4 | -1 \(-3, -6, **-1**\) | 2 \(**2**,  -3, -3\) | 0 \(-2, **0**, -5\) | -2 \(-4, **-2**, -7\) |
| **Y** | -6 | -3, \(-5, -8, **-3**\) | 0 \(-2, -5, **0**\) | 1 \(1, -2, -2\) | -1 \(**-1**, **-1**, -5\) |

_**Note: **Two alignments with the same score are possible here._

##### **Backtrace 1**

|  |  | W | H | A | T |
| :--- | :--- | :--- | :--- | :--- | :--- |
|  | 0 | -2 | -4 | -6 | -8 |
| **W** | -2 | **1** |  |  |  |
| **H** | -4 |  | **2** | **0** |  |
| **Y** | -6 |  |  |  | **-1** |

**Alignment:**

```
WHAT
||
WH.Y
```

##### **Backtrace 2**

|  |  | W | H | A | T |
| :--- | :--- | :--- | :--- | :--- | :--- |
|  | 0 | -2 | -4 | -6 | -8 |
| **W** | -2 | **1** |  |  |  |
| **H** | -4 |  | **2** |  |  |
| **Y** | -6 |  |  | **1** | **-1** |

**Alignment:**

```
WHAT
||
WHY.
```

##### 2.3 Smith-Waterman

**Find the best alignment between the sequences “WHAT” and “WHY”, using the Smith-Waterman algorithm, with +1 for a match, -1 for a mismatch, and -2 for a gap.**

_**Note:** In each row all value are written in brackets in the following format \(fromDiagonal, FromLeft, FromTop\). The chosen value is entered in the box_

|  |  | W | H | A | T |
| :--- | :--- | :--- | :--- | :--- | :--- |
|  | 0 | 0 | 0 | 0 | 0 |
| **W** | 0 | **1** \(**1**, -2, -2\) | **-1** \(**-1**, **-1**, -2\) | -1 \(**-1**, -3, -2\) | **-1** \(**-1**, -5, -2\) |
| **H** | 0 | -1 \(**-1**, -2,** -1**\) | 2 \(**2**, -3, -3\) | 0 \(-2, **0**, -3\) | -2 \(**-2**, **-2**, -3\) |
| **Y** | 0 | -1 \(**-1**, -2, -3\) | 0 \(-2, -3, **0**\) | 1 \(**1**, -2, -2\) | -1 \(**-1, -1**, -4\) |

_**Note: **The same alignment as before are possible to align the full sequence. However, since we only want to align a local sequence, we can just start with the highest score we find in the matrix and backtrace only this **subsequence**. _

**Possible Subsequences Alignment:                                    
**Since, we did not have a substitution matrix, which compiles the likelihood of randomly aligning sequences into the the alignment algorithm, we cannot say for sure what is better: Aligning 2/4 residues or aligning a subsequence of 2/2.

```
WH
||
WH
```

##### 



