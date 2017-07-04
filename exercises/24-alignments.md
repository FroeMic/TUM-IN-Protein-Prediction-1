## 2.4 Alignments

###### 01.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170601_PP1_alignment.pdf) \| [Wiki](https://i12r-studfilesrv.informatik.tu-muenchen.de/sose17/pp4cs1/index.php/Alignments)

---

#### 1. Keywords

##### Pairwise alignments: global, local \(Needlman-Wunsch / Smith-Waterman\)

**Goal:** Find the arrangement of residues that minimizes / maximizes the scoring function  
**Biology:** Try to maximize the overlap between the sequences

**Parameters:**

* Substitution matrix \(for each pair\)
* Gap Penalties \(linear, affine\)
* global, free-shift, local



##### Dynamic programming as solution for cascading recursion, Backtracking

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

##### 2.3 Smith-Waterman



