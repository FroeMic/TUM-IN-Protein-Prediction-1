## 1.3 Alignments 1

###### 11.05.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170511_alignments1.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=-yN2iBQnzeQ&index=3&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J)

---

#### 1. Recap

> **Sequence** leads to **Structure** leads to **Function**

**Question:** Why compare 3D shapes, when we are after function? Why not compare function?

> Because ...
>
> * we cannot compare function directly
> * structure is related to function
> * we CAN compare 3D structures
> * sometimes: similar structure -&gt; similar function

**Question:** How do we get protein 3D shapes?

> * primarily by experiment \(most accurate\)
> * computational biology \(most inferences\)

**Question:** How much does it cost to experimentally determine the 3D shape of a protein?

> Today it costs on average about 100 000 $ per protein.

#### 2. Tree of Life

* #### All life is related \(common ancestor\)
* 3 sections of tree of life
  * prokaryotes
    * \(unicellular\) bacteria
    * archaea
  * eukaryotes \(plants, animals, ... \)

**Homology: ** Here \(in the context of genes\), it describes proteins originating from a common ancestor.

**Definition of Species:** We are talking about two different species, once they cannot produce fertile offspring together. \(Example Bono an Chimpanzee\)

**Question: **What are the 3 sections found in the tree of life?

> bacteria, archaea, eukaryotes

**Question: **What does Homology stand for?

> Here \(in the context of genes\), it describes proteins originating from a common ancestor. It is also frequently used to describe 'similar structure' for genes / proteins.

**Question: **Why do linear gap penalties do models the reality of related genes / proteins well?

> With a linear gap penalty \(N gaps cost N\*x\) equally distributed gaps would be as expensive as clustered gaps. Biologically, gaps clustered to blocks, are however far more likely to occur, while the protein maintains similar structure / function.  
> It is more realistic to use an **Affine gap penalty** with higher costs for opening a new gap.



#### 3. Pairwise Sequence Comparison

###### Correct alignment: We need an objective function

* simplest objective function: percentage of letters which are identical
* more complicated functions describing a match 

BUT: the match score itself ignores, what we are after - biological similarity in function

##### Alignment

_To find the optimal superposition of two sequence, it is first necessary to define what 'optimal' means._

**Global Alignment:**

* Align all residues from the beginning to the end
* Needleman-Wunsch

**Local Alignment:**

* Best match for locally aligned regions
* Smith-Waterman

###### How do we align 2 sequences?

_Basically brute force: Visually \(moving around\), computationally \(dynamic programming\)_

Dynamic Programming Algorithm: See [Exercise 2.4 Alignments](/exercises/24-alignments.md)

**Gap insertion penalty:** Each wildcard \(gap\) used when aligning 2 sequences has a certain cost.

* Linear gap penalty: N gaps cost N\*x
* Affine gap penalty: opening gaps become more expensive
  * Gap open: cost 10x
  * Gap extension \(elongation\): costs x

##### Local vs Global Alignment: What is better?

**Question: **What is better? High sequence identity of a short \(local\) sequence, or worse sequence identity when matching a longer sequence? How can we decide?

> Compile the probability of randomly matching a sequence considering the background distribution. The result of this would be a substitution matrix such as BLOSUM62.

**Question: **Is identity the best way to match two sequences?

> Not necessarily: What we really find is similar biological function. Some amino acids might have similar biophysical features and could be swapped without any significant influence on the structure of the protein. Such matches should also be considered 'postive'.
>
> Building a scoring matrix based on evolutionary conserved residues does optimize the algorithm. \(e.g. BLOSUM62\)

###### BLOSUM62

![](/assets/Screen Shot 2017-07-01 at 23.19.39.png)Today many more substitution matrices exist.

**Interactive Tool to practice dynamic programming: **[http://melolab.org/sat](http://melolab.org/sat)

**Question: **Does dynamic programming give the best solution?

> Yes, dynamic programming produces one optimal solution. \(There could be others, though\)

**Question: **What are issues with dynamic programming?

> * Time used: O\(n^2\)
>   * Especially a problem, when comparing one protein agains the entire database.
> * How to choose parameters?
>   * Gap penalties
>   * substitution matrix

**Question: **What is the biological assumption behind an insertion when comparing sequences?

> Through evolutionary changes in the DNA \(e.g. a point mutation\) a new bump \(= amino acid\(s\)\) was introduced. Implicitly it is also assumed similar structure -&gt; similar function.



#### 4. Multiple Sequence Comparison



