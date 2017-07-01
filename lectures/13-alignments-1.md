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

#### 2. Pairwise Sequence Comparison

###### Correct alignment: We need an objective function

* simplest objective function: percentage of letters which are identical
* more complicated functions describing a match 

BUT: the match score itself ignores, what we are after - biological similarity in function

###### Local vs Global Alignment

_To find the **optimal** superposition of two sequence, it is first necessary to define what 'optimal' means._

**Global Alignment:** Align all residues from the beginning to the end

**Local Alignment:** Best match for locally aligned regions

###### Tree of Life

* All life is related \(common ancestor\)
* 3 sections of tree of life
  * prokaryotes
    * \(unicellular\) bacteria
    * archaea
  * eukaryotes \(plants, animals, ... \)

**Homology: ** Here \(in the context of genes\), it describes proteins originating from a common ancestor.

**Question: **What is the biological assumption behind an insertion when comparing sequences?

> Through evolutionary changes in the DNA \(e.g. a point mutation\) a new bump \(= amino acid\(s\)\) was introduced. Implicitly it is also assumed similar structure -&gt; similar function.

**Question: **What are the 3 sections found in the tree of life?

> bacteria, archaea, eukaryotes

#### 3. Multiple Sequence Comparison



