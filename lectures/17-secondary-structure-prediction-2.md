## 1.7 Secondary Structure Prediction 2

###### 01.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170601_sec2.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=RaMUi10-WmM&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=6)

---

#### 1. Recap

**Goal of Structure Prediction:** Predict the 3D structure and function from an input sequence.

**Proteins: **

* are formed by stringing up amino acids in a chain
* amino acids are between 35 to 30.000 residues long
* amino acids form substructures, called domains in order to fold
* in principle: a domain put into solvent \(water\) folds on its own and adopts a unique 3D structure

**Zones: **There are different 'zones' by percentage of sequence identity, in which we can identify similar structures

* **Daylight-Zone** \(100 % - 40%\)
  * Sequence - Sequence Alignment
  * Assumption: sequence similar -&gt; structure similar
* **Twilight-Zone **\(40% - 20%\)
  * Sequence - Profile Alignment
  * more distant relationships
* **Midnight-Zone** \(20% - 0%\)
  * Profile - Profile alignment
  * even more distant relationships

**Global and Local Alignment:**

**Question: **Relate the terms **Local** and **Global alignment** to the terms **Sequence-Sequence** and **Sequence-Profile**.

> Global alignments refers to aligning sequences \(proteins\) from start to end. Local alignments refers to only aligning parts of the sequences \(e.g. 50 residues\).  
> Throughout Sequence-Sequence, Sequence-Profile and Profile-Profile methods both global and local alignment can be used. I practice mostly local alignment is done.

**Comparative Modeling:**

* Idea:
  * Find a similar sequence with known structure in the PDB \(in the daylight-zone\)
  * Try to use the known 3D structure of the similar protein to model the structure of the unknown protein
  * fix physical / chemical errors of the predicted 3D structure and find most plausible 3D structure
* Reliably predicts **over 40 million proteins**
* However, for **most residues comparative modeling cannot be applied**

#### 2. Secondary Structure Prediction

Secondary Structure Prediction happens in 1D, 2D and 3D. The following chapter will mainly be about 1D Secondary Structure Prediction.

**DSSP** \(Define Secondary Structure of Proteins\) algorithm: Has 8 states

* **H** =** **Helix
* **G** = $$3_{10}$$ Helix
* **I**  = Pi Helix
* **E ** = Extended
* **B** = Beta-bridge, single-strand residue
* **S **= bent
* **""** = loop

**Local Sequence determines secondary structure**!

* Certain local sequence always form the same secondary structure \(⍺-helix, β-strand, loop\).
* Others \(penta-peptides\) are found in 2 different state, **dependent on their environment**

**Question:** What would be a simple method to predict secondary structure?

> 1\) Take known structure  
> 2\) Find longest consecutive run of motifs that **ONLY** occur in one of the 3 states: H \(Helix\), E \(Strand\), O \(Other\)  
> 3\) Check unknown sequence against found motifs

**Question**: What was the first secondary structure prediction method?

> Assuming that a **Proline** would break a helix, the occurrences of proline in a sequence was used to predict helices.

#### 3. 1st Generation Secondary Structure Prediction

💡 **Idea:** Build a frequency table over all amino acids, how often they occur in the secondary structure states based on the proteins where the structure is known.  
**Important:** Bias reduction, to make the set table representative for future. Remove all proteins in comparative modeling range.

1. find a unique subset of proteins with known 3D structure \(PDB\)
2. convert 3D to 1D \(secondary structure\) with DSSP

**Question:** Where do we get the secondary structures from?

> From the DSSP, which defines 8 states in total based on H-bond patterns.

**Question:** What is the 1st generation of secondary structure prediction based on? What was the accuracy? Was is successful?

> * Based on single residues
> * Between 50% and 55% accuracy \(Q3\)
> * Clearly better than random - so it can be considered a success

##### How can we measure the performance of secondary structure prediction?

❗️ **Q3:** three-state per residue accuracy


$$
Q3 = \frac{number\ of\ correctly\ predicted\ residues\ in\ states\ helix,\ strand,\ other }{number\ of\ residues\ in\ protein}
$$


**Question: **How can the performance of secondary structure prediction be measured?

> One way to do it, would be to calculate the **Q3** accuracy of a method against a test set. The Q3 accuracy is the **number of correctly categorized residues into one of the categories helix, strand, other divided by the total amount of residues.**

#### 4. 2nd Generation Secondary Structure Prediction

**Question:** How did the second generation of secondary structure prediction improve? Name one algorithm.

> Instead of using only single amino acids, it would consider a sliding window of the residues around a center amino acid.  
> **Example:** GORIII, with a Q3 accuracy of 55% - 60%

**Question:** What were problem of secondary structure prediction until 1994?

> * the maximum accuracy of predictions was expected to be 65%
> * β-sheet prediction was below 40%
> * many predicted segments where too short to appear in nature

#### 5. Introduction: Neural Networks

**Goal: **Use the representation of a set of examples \(training set\) for which the mapping _input -&gt; output_ is known to iteratively refine the weights of the connections betweens output and input units so that the error is minimized.

**Principles of neural networks**

* Free Variables: $$Connections\ \{J\}$$
* Output: $$out_i = \sum_{i=1}^{N^{in+1}} J_{ij} in_j$$
  * $$in_j $$ value of input unit $$j$$
  * $$out_i$$ value of output unit $$i$$
  * $$J_{ij}$$ connection between input unit $$j$$ and output unit $$i$$
* Error: $$E = \sum_{i=1}^{N^{out}} {(out_i - des_i)}^2$$
  * $$out_i$$ value of output unit $$i$$
  * $$des_i$$ secondary structure state observed for central amino acid for output unit $$j$$

**Training: **Change of connections $$ \{J\}$$ such that $$E$$ decreases \(e.g. gradient descent\)

**Problem:** Overtraining - happens if the network becomes too specific to the actual training set and looses accuracy for predicting unknown input. The point when to stop training can be found by using **cross-training, testing, validation sets**.![](/assets/Screen Shot 2017-07-02 at 12.53.59.png)

**Cross-Validation**: Split your available dataset into 3 sections

1. **Training** \(50%\): used to train ML algorithm
2. **Cross-Train **\(25%\): used to find threshold when to stop training and tweak parameters
3. **Testing** \(25%\): used ONLY to assess performance / accuracy of final ML algorithm

**Question:** How can the introduction of a new hidden layer in a neural network be described by means of a simple graph?

> Each new hidden layer basically introduces a new 'decision line' which can separate datapoints into different categories.

**Question:** What is cross-validation in the context of Machine Learning and why do we need it?

> Cross Validation in a method for estimating the performance of a predictive model \(e.g. a neural network\). To use it, the available dataset is split in 3 categories, 1\) a training set, 2\) a cross-training set and 3\) a test set.  
> 1\) The training set is used to train the model  
> 2\) The cross-training set is used to estimate the performance of the model after x training steps  
> 3\) The test set is used to assess the final performance of the model after training is finished  
>   
> The cross-training set is needed to decide, when to stop training \(when overtraining sets in\) and to tweak certain parameters before running against the test-set.

#### 6. Neural Networks for Secondary Structure

**Goal:** Solve the 3 problems at the time \[1\]  accuracy, \[2\] strand performance, \[3\] short segments![](/assets/Screen Shot 2017-07-02 at 13.35.52.png)

**Input: **13 \* 21 input units

* 13 ?? ❓
* 20 amino acids + 1 spacer

  However, the final accuracy was only about **62%**

###### Balanced Training:

* Helices are overrepresented in the training data
* Choose the training data, so all 3 states \(helix, strand, other\) are equally represented

**Result**

* overall accuracy dropped to **60%**
* β-sheet prediction improved from **40% **to around **60%**

#### 7. PHDSec: Structure to Structure Prediction

We still have the problem of bad segment prediction \(too short segments\). This is due to the fact that samples from the database are selected at random, loosing information about local correlations.

How can we get information about the local correlation \(e.g. length of a helix\) into the prediction model?

**Solution:** Add a second Neural Network, which takes the predicted sequences from the first network as input.

**BUT:** Accuracy was still only 60% + ε



