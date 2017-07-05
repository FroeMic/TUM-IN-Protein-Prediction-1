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

* actual secondary structure of amino acid depends on the local sequence \(context\)
* even identical stretches \(up to 5 aa\) can occur in different secondary structures
* which structure is preferred depends on the available **hydrogen bond **opportunities
* more hydrogen bonds =&gt; more stable
* **Chou-Fasman**
  * simply look a the frequency an amino acid occurs in each secondary structure
  * search for **nucleation regions**
    * for helix: 4 out of 6
    * for sheet: 3 out of 5
  * extend until a window of 4 amino acids drops below 1
  * turns also check for Proline and Glycine
  * More info, in case this was not enough to understand: [https://en.wikipedia.org/wiki/Chou%E2%80%93Fasman\_method](https://en.wikipedia.org/wiki/Chou–Fasman_method)
* **GOR I**
  * 17 amino acid window
  * considers the state of 8 aa neighbors on each side \(bayesian\)
  * builds on three matrices \(17X20\) for helix, sheet and coil
  * \(the original 'turn-matrix' was removed since it showed too high variability for a window of 17 aa\)
  * thresholds: 
    * 4 amino acids for helix
    * 2 amino acids for sheet
* **GOR III**
  * in addition for GOR I it considers all pairs with on the sliding window \(= segment\)
  * still not good for sheets, since the could be formed by non-local interaction
* **PHDxxx**
  * usage of **local evolutionary information** in the form of sequence profiles generated from multiple alignments
  * usage of global features \(length, aa composition, ...\)
  * the use of **redundancy-reduced**, **balanced data set** for training can be useful
* **PHD\(-acc, -sec, -htm\)**
  * add a second layer of networks \(PHDsec\)
    * L1: sequence residue -&gt; secondary structure  of that resisude
    * L2: secondary structure state -&gt; secondary structure state for consolidated \(smoothened\) predictions
  * create a **jury** between balanced and unbalanced trained networks and different output states

##### Performance Assessment

* Precision, Recall, Accuracy
* Qx-Measure: For x states, fraction of correct predictions \(TrueNegative + TruePositives\) of all predictions
* Significance?
  * determine the average Q on you dataset
  * calculate the standard deviation \(sigma\)
  * calculate the standard error \(sigma / sqrt\(N\) \)
  * N is size of test set
* Compare Methods
  * compare always on the same instances
  * test / training split have to be the same for both tools
  * not overlap allowed between test and training set \(structures in comparative modeling range violate this\)
  * alternative: compare on fresh data published after publication of methods

##### Membrane Proteins

##### HSSP Curve

#### 2. Exercises

#### Questions

**Question:** How does ClustalW work? How does it differ from BLAST?

> ?

**Question:** What is HHblits?

> ?

**Question:** What is the definition of accuracy? Is it the same as Qx?

> ?



