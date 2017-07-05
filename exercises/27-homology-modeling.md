## 2.7 Homology Modeling

###### 29.05.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170629_PP1_secstruc_pred.pdf) \| Wiki

---

#### 1. Ideas and Keywords

##### Ideas

* Sequence Determination \(short: sequencing\) of DNA is highly automated today and very cheap

* Computer programs can help identify genes and coding regions
* From coding regions you can infer the protein sequence \(1D information\)
* **The entire sequencing process is cheap and quick, everything after that isn't.**

##### Available types of Data

* sequences \(1D information\)
* Annotations of already investigated proteins
* \(few\) protein structures \(3D information\)
* **Goal:** clever combination to infer more knowledge about yet unknown protein

##### Additional Tools / Databases

* UniProtKB, PDB
* Blast, Smith-Waterman
* PSI-Blast, ClustalW/CluastlX, MaxHom, SAM / HMMer, T-Coffee 
* HHblits: SSearch, PSI-Search

##### Homology / Comparative Modeling

* **Goal**: Direct link from 1D to 3D structure \(this would be the ultimate jackpot, but it does not work so far\)
* Work around: Borrow structure from already know, sequence-similar proteins
* Tools: Modeller, Swiss-Model
* **Modeller**
  * uses a set of **spatial restraints** applied as PDFs \(probability density functions\)
    * $$C_{\alpha} - C_{\alpha}$$ distances
    * main chain $$N-O$$ distances
    * main-chain and side-chain dihedral angles
  * Which PDFs? Derived from analysis of 17 homologous protein families
  * needs a related template with a known 3D structure
  * Features
    * models non-hydrogen molecules
    * de-novo \(?\) prediction of loops
    * local installation
  * **Typical steps**
    * 1\) identify templates / fold recognition
    * 2\) align
    * 3\) model
    * 4\) assess
    * 5\) refine
* **Swiss-Model**
  * originally: fully automated, little user interaction
    * 1\) selection of templates
    * 2\) modeling \(copying coordinates\)
    * assessment
  * now: more interactive and sophisticated model assessment
  * sever based service
  * convergent evolution with Modeller

##### Secondary Structure Prediction



##### Membrane Proteins



##### HSSP Curve





#### 2. Exercises

#### Questions

**Question:** How does ClustalW work? How does it differ from BLAST?

> ?

**Question:** What s HHblits?

> ?



