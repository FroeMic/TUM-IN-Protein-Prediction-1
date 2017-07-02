## 1.10 TMSEG

###### 20.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1i_20170620_tmseg_bernhoferm.pdf) \|[ Lecture Recording ](https://www.youtube.com/watch?v=uhqBFFuba6o&index=9&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J)

---

#### 1. Introduction TMSEG

##### 1.1 Rational: Why another predictor

* More Data available
* Less expensive machine learning \(more computing power available\)
* Improve runtime

##### 1.2 Dataset

* 166 membrane protein sequences after redundancy reduction
* Data curated and linked from several databases \(PDB, OPM, ...\)
* 1441 proteins from the SignalP Training Set

  * 1142 soluble \(after RR\)
  * 199 membrane \(after RR\)

* **Split Dataset into 4 subsets**

  * each set maintaining distribution of TMPs, SPs and sequence length
  * use 3 sets for **cross-validation**
  * use 1 set for final independent evaluation \(**blind set**\)

#### 2. TMSEG Prediction

**Intro: Classification Trees and Random Forest**

###### Classification trees

* Given $$N$$ training samples and $$M$$ inout features find the best recursive partitioning to predict the class labels in the leaf nodes
* Approaches differentiate algorithm: splitting, pruning, balancing, ...

###### Random Forest

_How does it work?_

* ensemble method: grow $$T$$ trees for a forest
* for $$M$$ input features choose $$m < M$$
* for each $$t \in T$$ 
  * Select $$N$$ training samples with replacement from all $$N$$ samples
  * At every split, choose $$m$$ random features. Use the best split among those to build the tree
* The final prediction uses the prediction of all trees

_Advantages_

* fast
* robust against overtraining
* no black box
* intuitive to interpret
* good performance

##### 2.1 Step 1 - Feature Sets

###### Initial Prediction

* Random Forest \($$T = 100, m = 9$$\)
* Sliding Window of 19 residues \($$w = 19$$\)
* 3 scores for each residue \(0 - 1000\)
  * Signal Peptide \(often mistaken for TMHs\)
  * TMH
  * Soluble

###### Feature Set

* **Global Features**
  * Global amino acid composition
  * Protein length
* **Local Features**
  * PSSM Score \(Position Specific Scoring Matrix\)
  * Distance to N- / C- Terminus
  * Average hydrophobicity \(Kyte-Doolittle\)
  * percentage of hydrophobic residues \(in window size $$w = 9$$\)
  * percentage of negative / positive charged residues \(in window size $$w = 9$$\)
  * percentage of polar residues \(in window size $$w = 9$$\)

##### 2.2 Step 2 - Empirical Filter

* smooth score with median filter \($$x = y$$\)
* Adjust scores to avoid overprediction
  * soluble += -185
  * TMH += -60
* Assign each residue the state with the highest score
* Remove signal peptides with &lt;4 residues
* Remove TMHs with &lt;7 residues

##### 2.3 Step 3 - Refine TMH prediction

* **Neural Network **\(25 hidden nodes\)
  * Input: TMH segments of variable segments of variable length
  * Features:
    * Amino acid composition
    * Average hydrophobicity
    * percentage of hydrophobic residues
    * percentage of charged residues
    * segment length
* Split long TMHs \(≥35 residues\) into 2 shorter TMHs \(≥17 residues\)
* Adjust TMH endpoints by up to ±3 residues

##### 2.4 Step 4 - Topology Prediction

* Random Forest \($$T = 100, m = 7$$\)
* Assign soluble segments to side 1 or 2
* Features

  * Amino acid compositon
  * percentage of positive charged residues
  * percentage of absolute difference of positive charged residues on side 1 vs side 2 

* **Only consider residues close to TMHs**

  * 15 residues nest to TMHs and 8 residues into TMHs

* Predict topology of N-Terminus and extrapolate

* if a SP is predicted, the residues after the SP are always 'outside' \(SP = Signal Peptide\)

**Question:** What are advantages of using a Random Forest?

> * Fast
> * robust against overtraining
> * no black box
> * Intuitive to interpret
> * good performance

#### 3. TMSEG Performance measures

```markdown
# Note: Per residue measures are often misleading!
#       => better score TMH segments
```

**Whole Protein Scores: **$$Q_{ok}$$ and $$Q_{top}$$ **=&gt; What is a correctly predicted TMH?**

* **Strict Criteria**
  * Endpoint deviation ≤ 5 residues
  * Overlap at \(observed / predicted\) at least 50%

###### How can we measure the performance on predicting Transmembrane Helices?

**Recall:** 
$$
r_i = \frac{correctly\ predicted\ TMHs}{observed\ TMHs}
$$


**Precision:** 
$$
p_i = \frac{correctly\ predicted\ TMHs}{predicted\ TMHs}
$$


$$Q_{ok}$$:


$$
Q_{ok} = \frac{100}{N} \sum_{i=1}^N x_i; x_i = \begin{cases} 1, & if\ p_i = r_i = 100\% \\ 0, & else 
 \end{cases}
$$


$$t_i$$:


$$
t_i = \begin{cases} 100\%, & \text{if topology correct}\\ 0, & else 
 \end{cases}
$$


$$Q_{top}$$:


$$
Q_{top} = \frac{100}{N} \sum_{i=1}^N y_i; y_i = \begin{cases} 1, & if\ t_i = p_i = r_i = 100\% \\ 0, & else 
 \end{cases}
$$


###### How can we measure the performance on distinguishing soluble proteins from transmembrane proteins?

**FPR:** 
$$
FPR = 100 * \frac{incorrectly\ predicted\ TMPs}{soluble\ proteins}
$$


**Sensitivity:** 
$$
Sensitivity = 100 * \frac{correctly\ predicted\ TMPs}{observed\ TMPs}
$$


```markdown
# Result: TMSEG has exceptionally low misclassification rates compared to other methods.
```

#### 4. Future Work

##### 4.1 Applying TMSEG to other methods

##### 

##### 4.2 Potential extensions

##### 



