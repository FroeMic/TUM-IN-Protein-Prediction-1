## 2.4 Alignments

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
* global, free-shift, local

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

**Dynamic Programming: **

1. **Setup matrix:**
   1. Template $$t$$ horizontal, Query $$q$$ vertical 
   2. Fill  the $$1^{st}$$ row / column 
      1. Needleman-Wunsch: with increasing gap penalties
      2. Smith-Waterman: with zeros
2. **For each row **$$m_i$$ \(top -&gt; down\)
   1. **For each position **$$m_{i,j}$$ \(left -&gt; right\)
      1. $$s_1 = m_{i-1,j-1} + SubstitutionMatrix(q_i, t_j)$$
      2. $$g_1 = m_{i-1,j} - GapPenalty$$
      3. $$g_2 = m_{i,j-1} - GapPenalty$$
      4. **Enter **$$max(s1,g1,g2)$$ **into the box and remember which score was selected**
3. **Backtrace**
   1. Find the maximum value in the matrix 
   2. Follow the path back to the origin and note down the aligment
      1. **Diagonal Step:** Match the corresponding residues
      2. **Step up**: Only take the Template-Value \(horizontal\), add a gap to the template sequence
      3. **Step Left:** Only take the Query-Value \(vertical\), add a gap to the template sequence

##### Substitution matrix: PAM, BLOSUM

##### Match, mismatch, gap

##### 

##### Sequence identity, similarity, conservation

##### 

##### E-value

##### 

##### FASTA format \(basic principle\)

##### 

##### One letter code for amino acids \(you do not have to learn the code, just know what it means\)

##### 

##### Homology, homologues/homologs

##### 

##### Multiple Sequence Alignments \(MSAs\)

##### 

##### Sequence profile, iterative profile creation

##### 

##### BLAST, PSI-BLAST

##### 

#### 2. Exercises

##### 2.1 Questions

**Question:** How can you define similarity between two protein sequences?

> ?

**Question: **What does "conservation" mean in the context of sequence alignments?

> ?

**Question:** Why are sequence alignments useful?

> ?

**Question:** What are the main differences in the algorithms of Global and Local alignment? Why does it make sense to not always perform a global alignment.

> ?

**Question:** Which amino acids can \(with high likelihood\) be substituted for Leucin without having an effect on protein function?

> ?

**Question:** Which substitution is more probable according to PAM250 and according to BLOSUM62: \[a\] W &lt;&gt; F \[b\] H &lt;&gt; R

> ?

**Question:** What is a multiple sequence alignment?

> ?

**Question:** What kind of sequences are likely to be used for an MSA? In which relationship are they to each other?

> ?

**Question:** Why would you want to align multiple sequences? What kind of information is contained in MSAs but not directly in e.g. all-against-all pairwise alignments?

> ?

**Question:** Given your knowledge of the algorithms for pairwise alignments, how could you calculate an MSA? Is that a feasible approach? Why?

> ?

**Question:** You have a sequence which you would like to find in a database. Which search method and which E-value cutoff do you use, \[a\] if you know your sequence is in the database and only want to find that entry \[b\] if you would like to find homologs.

> ?

**Question:** What is the difference between BLAST and PSI-BLAST?

> ?

##### 2.2 Needleman-Wunsch

**Find the best alignment between the sequences “WHAT” and “WHY”, using the Needleman-Wunsch algorithm, with +1 for a match, -1 for a mismatch, and -2 for a gap.**

##### 2.3 Smith-Waterman

**Find the best alignment between the sequences “WHAT” and “WHY”, using the Smith-Waterman algorithm, with +1 for a match, -1 for a mismatch, and -2 for a gap.**

