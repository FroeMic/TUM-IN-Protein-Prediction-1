## 1.2 Introduction: Structure

###### 04.05.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170504_intro2_structure.pdf) \| [Lecture Recording ](https://www.youtube.com/watch?v=8g0G5C4rRNA&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=2)

---

#### 1. Recap

**Common to Life:** DNA / Cells

**Proteins:** Machinery of Life - they do everything that needs to be done

* about **85 Million **known protein sequences
* about 120 000 known 3D structures of proteins in PDB
* between 20.000 and 25.000 proteins in a typical human
* protein length \(in amino acids\): 35 - 30.000, with a median around 400

**Central Dogma / Informationflow:** DNA -&gt; RNA -&gt; Proteins![](/assets/Screen Shot 2017-07-01 at 19.42.14.png)**Translation:** Proteins are made up of amino acids \(20 different kinds\). Each amino acids is encoded by a nucleotide triplet \(codon\) of DNA / RNA.

#### 2. Proteins and Domains

```markdown
# It is important to realize that every representation of a protein (sequence, image, ...) is 
# only a representation of reality.
```

##### 2.1 Amino Acids

Proteins are built up out of a chain of amino acids. These amino acids are joined into a **linear polypeptide chain**, a protein. Each protein is therefore a combination of the **20 different types of amino acids.**

![](/assets/Screen Shot 2017-07-01 at 19.54.01.png)

* Each **residue** \(amino acid\) in this chain has a backbone and a side chain
* Different amino acids have **different side-chains**
* Each amino acids has **the same backbone**, along which they are chained
* Proteins are always chained up from the **N-Terminus **to the **C-Terminus** in a condensation reaction 
  \(a H20 molecule is released\)

###### Side Chains

Amino acids only differ in their side chains. These side chains determine the chemical properties of the respective amino acid. There are the following _features_ an amino acid can have:

* polar \(hydrophilic, likes water\)
* non-polar \(hydrophobic, avoids water\)
* acidic \(negatively charged\)
* basic \(positively charged\)

**Question: **How many different amino acids are there?

> 20

**Question: **How do amino acids differ? What do they have in common?

> Different amino acids have different side-chains, which influence the chemical features of the respective amino acid. All of them share the same backbone.

**Question: **In which different feature groups can you categorize amino acids?

> polar, non-polar, acidic \(negatively charged\), basic \(positively charged\)

**Question:** Draw the basic chemical structure of an amino acid.

```
H   R   O
 \  |  //
  N-C-C
 /  |  \
H   H   O-H
```

**Question:** How are amino acids linked together to form a protein?

> In the translation process, a **Ribosome **translates a **mRNA** strand to a protein, by decoding the RNA triplets into amino acids and then linking the amino acids by peptide bonds. They chaining ALWAYS happens from the **N-Terminus **to the **C-Terminus  **releasing an H20 molecule as part of the reaction.

##### 2.2 Protein Structure

> ###### What is a gene?

A gene is a region of DNA, which contains all information for the creation of an entire RNA strand. \( = protein\)![](/assets/Screen Shot 2017-07-01 at 20.26.17.png)**UTR: **Untranslated region \(leader sequence, header sequence\)

**Exon:** Part of a gene that will encode a part of the final mature RNA \(and thus protein\)

**Intron:** Part of a gene that will be removed by **RNA Splicing** before the protein is translated

##### 2.3 Domains

**Definition**: _If I took a sequence out of a protein, string it up and put it into solvent, it adopts a unique 3D structure on its own._

Proteins are built out of several such substructures. The question is **Can we guess domains from sequence?                                  
**By aligning and comparing proteins with know 3D structure, it is possible to find common, overlapping domains that adopt the same 3D structure across different proteins.

**Question: **What is the definition of a 'domain'?

> A domain is a protein sequence, which when put into solvent adopts a unique 3D structure on its own.

**Question: **How many domains does a protein have?

> * 61% of proteins in the PDB are single domain
> * 28% of proteins in the PDB are in 62 proteomes
>
> **Problem: **This is a biased view on proteins. The 3D structure of Single-Domain-Proteins is easier to experimentally determine, so more Single-Domain-Proteins have been analyzed.

**Question: **Can domains overlap?

> Yes, it can happen. However, it is not what is typically observed** .**

#### 3. 3D Comparisons

There are many different methods for 3D alignments. The points is that comparing 3D structures is highly non trivial and ultimately comes back to the intuition about comparing 3D objects.

**Question: **How can we compare 3D structures?

One solution would be to align the corresponding residues of both sequences / 3D structures and take the **Root Mean Square Deviation**. \(If one pair lies very far apart, it will result in an extremely low score\)

> $$RMSD(A,B)= \sum_{i=0}^n ({r_i}^a - {r_i}^b )^2$$
>
> If the score is below a certain threshold, it is a match, otherwise it is not.

**Question: **How can align and compare the structure of 2 proteins?

> 1\) Find the corresponding points \(residues that match in 3D\)  
> 2\) Find Superposition independent of domain movements and calculate score \(e.g. RMSD\)

**Question: **Why is global protein comparison most of the time impossible?

> The definition of protein enforces a per residue comparison \(no scaling\). Hence only proteins of the \(almost\) the same length can be compared globally. Since proteins are between 35 and 30.000 residues long, global comparison does not make sense in most of the cases.

**Question: **What is the difference between global and local alignment?

> In **global alignment** two structures / sequences are compared from beginning to end \(compare the whole thing\).  
> In **local alignment** however, subunits \(domains\) of the proteins are aligned. \(Problem: What is a valid unit? Where to cut?\)

**Question: **How to decide what is a valid unit for local comparison of 2 proteins?

> ❓ \(I couldn't identfiy a valid answer in the lecture recording\)

**Question: **Which comparison not using cartesian RMSD could be used for comparison?

> 2D distance map: difference of differences. Only information about the chirality \(mirror image\) is lost.



