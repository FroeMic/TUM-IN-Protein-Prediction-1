## 2.3 Protein Structure

###### 18.05.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170518_PP1_poteins.pdf) \| [Wiki](https://i12r-studfilesrv.informatik.tu-muenchen.de/sose17/pp4cs1/index.php/Protein_structures)

---

#### 1. Keywords

##### Amino acids, side chains, residues

* 20 different amino acids
* **Backbone:** all of them have the same backbone \(see following picture\)
* **Side Chain:** the differ in their side-chains, which also give them unique features. 
  * electrically charged side chains \(positive or negative\)
  * polar uncharged side chains
  * hydrophobic side chains
  * special cases
* Amino Acids are the building blocks of proteins. Once it is part of a protein, the amino acids are referred to as a residues

![](/assets/Peptidformationball.svg.png)

##### Protein sequence

* linear sequence of amino acids \(residues\), connected by their backbone
* formed by a condensation reaction \(formation of a peptide bond, under creation of a water molecule\)
* oriented from **N-Terminus** to **C-Terminus**
* typically starts with **Methionine \(AUG codon\)**

##### Secondary, tertiary, quaternary protein structure

* **Secondary Structure**
  * local structure elements: **⍺-helix, β-sheet, loops**
  * building blocks for higher order structures
  * stabilized by **hydrogen bonds**
  * amino acids have 'preferences' for certain secondary structure elements
* **Tertiary Structure**
  * spatial arrangement of secondary structure elements of a protein
  * alternative arrangements can exist
  * can be used to **hierachicaly organize** found proteins
* **Quarternary Structure**
  * formation of **multi-protein complexes**
  * difficult to determine precisely

| Coding / Representation | Protein Aspect |
| :--- | :--- |
| **1D Information**: sequence of amino acids as a string | **Primary Structure**: amino acid sequence |
| **2D Information:** 2D-Array, contact map | **Secondary Structure:** helices, sheets, ... |
| **3D Information:** coordinates or atom couplings | **Tertiary Structure:** Spatial arrangement of secondary structure elements |


##### Hydrogen bonds

* **weak** bond between H-atom \(donor\) and **O** or **N** atom
* Distance: $$160 - 200\ pm$$ \(relatively large distance\)
* stabilize secondary structure formations

##### Alpha helix, beta sheet, loop, random coil, disordered region

* **Alpha Helix**
  * **3,6 amino acids** per turn, spiral forming
  * typically **4-40** residues long
  * stabilized by hydrogen bonds between backbone atoms
* **Beta Strand / Sheet**
  * Several **parallel** or **anti-parallel** strands form a sheet
  * 'long-range' hydrogen bonds \(in terms of residues involved\)
  * 'flat'

* **Loop / Turn / Coil**

  * connector between undefined secondary structure elements
  * end / start of polypeptide chain

* **Disordered Region / Random Coil**

  * no clear secondary structure elements identifiable
  * like 'statistical distribution' of shapes
  * biologically: 'adapter' to different target shapes, which stabilize upon contact with partner

##### Protein features

* Size
* Amino Acid Composition
* Surface Area 
* Hydrophobicity
* Solvent accessibility
* Binding Sites / Active Binding Sites
* Iso-Electric Point

##### Ramachandran plot

When chaining up the amino acids on the polypeptide bond, the main bond $$\omega_+$$is rather rigid and cannot rotate. The two bonds around the center atom \($$\phi,\ \psi$$\) of each amino acid, however are free to rotate \($$-180,\ +180$$ \). However, these rotation angles are subject to certain constraints \(due to e.g. the side chain of the amino acid\)

A **Ramachandran Plot** plots the typical / allowed regions for **⍺-helices** and **β-sheets**.![](/assets/Screen Shot 2017-07-04 at 16.57.03.png)


##### Classification of Structures

Two similar methods \(CATH / SCOP\) both aiming to **organize** the protein structures available in the PDB based on **single domains.**

* Hierarchical System
  * Secondary Structure Content
  * Fold
  * Super Families
  * Families

**SCOP:** Structural Classification Of Proteins
 * fully manually curated, driven by expert analysis

**CATH:** \(Class, Architecture, Topology, Homologous Superfamily\)
* semi-automatic procedure for deriving a novel hierarchical classification of protein domain structures
* 4 main levels
  * **Protein Class:** Mainly secondary structure composition of each domain 
  * **Architecture:** Summarizes shapes based on orientation of secondary structure elements
  * **Topology:** Sequential connection considered
  * **Homologous Superfamily:** High similarity with similar functions, evolutionary relationship assumed
* **Numbering Scheme**
  * C: \(Alpha, Beta, Alpha/Beta\) +1
  * A: Same Architecture, different Topology \(31\) + 10
  * T: Topology \(connection of 2ndary structure elements\) \(505\) +10
  * H: Homology \(families\)\(645\) +10

##### Protein domain, PFAM

* **PFAM - Protein Families Database**
* focus on **single domains**
* 559 clans, 16295 families
* **PFAM-A**
  * manually curated
  * HMM profiles for seed alignment
  * HMM profiles for full alignment
* **PFAM-B:** Automatically created

**Family:** Collection of related protein regions  
**Domain:** Structural Unit  
**Repeat:** short unit, unstable in isolation, but forms stable structure when found in multiple copies  
**Motif:** short unit found outside globular domains  
**Clans:** related group of PFAM family entries

##### Protein Data Bank \(PDB\)

* collection of high resolution protein structures \(120 000 entries\)
* **X-Ray Crystallography, NMR, Cryo-EM**
* slowly growing
* different quality of data

##### Root mean square deviation \(RMSD\)

Measure to determine **3D similarity** between structures

1. Superimpose
2. Align sequences to 'guess' corresponding residues
3. Calculate the distances \(mostly $$C_\alpha$$\)

##### Protein Function

* **Gene Ontology \(GO\)**
  * controlled vocabulary
  * hierarchically structured
  * 3 Main Sections
    * cellular component
    * molecular function
    * biological process
* **Enzyme Commission Number**
  * Numerical Classification of enzymes
  * Based on chemical reactions the catalyse
  * recommends enzyme name
  * does not imply any evolutionary relation

#### 2. Exercises

##### 2.1 Questions

**Question:** What are the building blocks of proteins?

> * Proteins are polypeptides, which consist of amino acids as building blocks

**Question:** Define protein backbone and amino acid side chain in 1 or 2 sentences for each term.

> * **Backbone:** All amino acids have the same with an N-Terminus on one and a C-Terminus on the other side by which they are chained up into a protein. \(Always read / write from N- to C-Terminus\) 
> * **Side Chain:** Each Amino Acid has a different side chain, which equips it with unique features \(length, polar, non-polar, electrically charged\)

**Question:** How many amino acids appear in proteins? How can they be classified?

> All proteins are built from **20 different amino acids**. The can be classified into the following 5 groups /categories
>
> * positively electrically charged side chain 
> * negatively electrically charged side chain
> * polar uncharged side chains
> * hydrophobic side chains
> * special cases

**Question:** Name atom types involved in a hydrogen bond. Do S-H groups form hydrogen bonds? Why \(not\)?

> Hydrogen bonds normally involve
>
> * an **H **atom \(obviously\) as donor
> * either an **O** or **N** atom as acceptor
>
> Due to its lower electronegativity Sulfur does not engage in classical Hydrogen-Bonds. \(However nonclassical hydrogen bonds with Sulfur seem to exist, according to literature\)

**Question:** How are alpha helices held together?

> Alpha-Helices are stabilized by **hydrogen bonds** along the backbone. Every turn takes about **3,6 **residues.

**Question: **What is similar and what is different in the hydrogen bonding of the alpha helix and the beta sheet?

> * Hydrogen bonds in **Alpha Helices** are 'ultra-local' and occur along the backbone of the helix \(each 3.6 residues\)
> * Hydrogen bonds between **Beta Sheets** happen between the beta-strands \(running parallel or antiparallel\) which can be rather far apart in sequence.

**Question: **Why do we find "forbidden" areas in a Ramachandran plot?

> The Ramachandran plot shows the angles $$(\phi,\ \psi)$$ of amino acids in which alpha-helices and beta sheet are typically observed. Forbidden areas are those that are not possible due to physical constraints due to e.g. the side chain of the amino acid.

**Question:** What is a protein domain?

> A domain is a conserved (sub-)sequences of a protein, which adopts a unqiue 3D structure when put into solvent.

**Question:** How many amino acids are typically found a in a domain? Why is there a minimum/maximum size?

> Proteins domains are found between 36 and 690 residues long. Most protein domains have a length of around 100 residues.
> 
> Minimum Size: ?
> Maximum Size: ?

##### 2.2 PDB

**Question:** How many structures are stored in the PDB? How many of those are protein structures?

> About 130 000 entries can be found in the PDB, of which around 120 000 are protein structures.

**Question:** Which experimental methods are \(mainly\) used to determine the structures? How long does it on average take to find the 3D structure for one protein for each method?

> The largest part (90%) of proteins structures are determined by X-Ray crystallography, followed by NMR (9%) and Cryo-EM (1%).
> However, the number of new Cryo-EM structures is projected to overtake the number of new NMR entries in 2017. Current sciene pushing the limits of Cryo-EM resolution, makes it a promising technology for future 3D structure determination.
>
> **Costs / Time per Method**
> * X-Ray: (100 000, ?)
> * NMR: (?, ?)
> * Cryo-Em: (?, ?)

**Question:** How many human \("Homo sapiens"\) protein structures are in the PDB?

> About 37 000 protein structures of homo sapiens. (Not, sequence unique entries though)

**Question:** Why does the number of protein structures already decreases when reducing at 100% sequence identity? Why does it decrease when reducing at even lower sequence identity further?

> * The PDB has redundant 3D structures for certain proteins from different experiments. This has different reasons such as competing groups, different research goals, better resolution.
> * Since most proteins developed under evolutionary pressure, large parts of proteins of the same family share a high sequence overlap.

##### 2.3 Molecular Visualization

```markdown
# Note: Neither mentioned in exercises nor lectures. Let's hope there is no question regarding this.
```



