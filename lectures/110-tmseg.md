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

_Advantages_

* Fast
* no black box
* Intuitive to interpret
* good performance



##### 2.1 Step 1 - Feature Sets

##### 

##### 2.2 Step 2 - Empirical Filter

##### 

##### 2.3 Step 3 - Refine TMH prediction

##### 

##### 2.4 Step 4 - Topology Prediction



**Question:** What are advantages of using a Random Forest?

> * Fast
> * no black box
> * Intuitive to interpret
> * good performance

#### 3. TMSEG Performance measures

#### 

#### 4. Future Work

##### 4.1 Applying TMSEG to other methods

##### 

##### 4.2 Potential extensions

##### 



