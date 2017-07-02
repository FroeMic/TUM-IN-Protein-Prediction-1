## 1.9 Membrane Structure Prediction

###### 13.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170613_tmh1.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=ZIQjVzvBN3E&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=8)

---

#### 1. Introduction Membrane

**Requirements for Cell Membrane**

* separate the content of the cell from its surroundings
* control traffic into and out of the cell
  * * keep malicious things out
    * let good things in
* must be a dynamic structure

**Main components of the cell membrane**

1. Carbohydrates
2. Cholesterol
3. Phospholipids
4. Proteins

##### Phospholipids

* form the barrier that separates the inside of a cell from the outside
* pospholipids are arranged in a **lipid bilayer**
  * **Inside: **fatty acid tails \(non-polar, hydrophobic\)
  * **Outside**: phosphate group \(polar, hydrophilic\)

##### Membrane Proteins

* Provide several functions to the cell
  * help to be recognized by immune cells
  * transport proteins control substance flow in and out of the cell
  * receptor proteins bind hormons, which can change cell function
  * provide structural stability
* Membrane proteins can \(easily\) shift around laterally 

**Membrane Proteins are especially important for drug targets**

```markdown
# Note
Similar to the membrane, proteins also tend to have a **hydrophobic core**. 
Membrane proteins however, tend to have a **hydrophobic outside** and an **hydrophilic core**.
```

**Question:** What are the requirements of a cell membrane?

> * separate the content of the cell from its surroundings
> * control traffic into and out of the cell
>   * keep malicious things out
>   * let good things in
> * must be a dynamic structure

**Question:** What are the 4 main structural components of the cell membrane?

> Carbohydrates, Cholesterol, Phospholipids, Proteins

**Question:** What is the cell membrane mainly made out of?

> The cell membrane is a so called **lipid bilayer** of **phospholipids**. Phospholipids have a non-polar, hydrophobic tail \(membrane center\) and a polar, hydrophilic head \(outside of membrane\).

**Question:** What are functions of membrane proteins?

> * help to be recognized by immune cells
> * transport proteins control substance flow in and out of the cell
> * receptor proteins bind hormons, which can change cell function
> * provide structural stability

**Question:** Can membrane proteins easily move around?

> It depends:
>
> * Membrane proteins can easily move laterally
> * But it is hard to move into / out of the lipid bilayer

#### 2. Introduction Transmembrane Helix \(TMH\)

Although membrane proteins are especially interesting for drug targets, there are only limited 3D structures to be found in the PDB. Mostly, because it is extremely difficult to put them into a crystal in their 'natural' membrane environment.

**There are essentially 2 important questions when it comes to TMH prediction:**

* How many helices go through the membrane?
* In which direction do they go through the membrane? \(topology\)

**Question:** Why are there so few membrane proteins in the PDB?

> It is particularly difficult to experimentally determine the structure of membrane proteins due to the special environment they naturally occur \(the membrane\).

**Question:** What are they key questions TMH prediction tries to answer?

> * How many helices go through the membrane?
> * In which direction do they go through the membrane? \(topology\)

#### 3. TMH Prediction

**Question:** Why could be a plausible reason why PHDSec failed for predicting transmembrane helices?

> Unlike 'normal' proteins, transmembrane proteins have an hydrophobic outside and a hydrophilic inside.

What could be a strategy to come around that? **Build up a hydrophobicity index.**

* There are different hydrophobicity scales, optimized for different problems

**Identifying hydrophobic regions**

* Whenever the hydrophobicity is over a certain threshold, consider it a membrane helices
* except the hydrophobic residues over \(the lower\) threshold are not long enough for a TMH \(20 residues\)

**Question:** How should we choose the threshold for the hydrophobicity?

> ❓

**Identifying Topology:** What is inside/outside of a TMH?

* **Positive Inside Rule:** Looking at the parts which connect TMHs within on protein, they look different depending on which side of the membrane they are: **There is a excess of positively charged residues on the inside.**



**Question:** What is the Positive Inside Rule and what is it used for?

> The positive Inside Rule is used to find the topology of transmembrane proteins: The loops connecting TMHs on the inside of the cell membrane have an **excess of positively charged residues**.



