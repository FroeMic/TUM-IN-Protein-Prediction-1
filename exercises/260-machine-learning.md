## 2.6.0 Machine Learning

###### 22.06.2017 \| [Slides ](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170622_PP1_ml.pdf "Slides")\| [Wiki](https://i12r-studfilesrv.informatik.tu-muenchen.de/sose17/pp4cs1/index.php/Machine_Learning_incl._Tricks_/_Secondary_Structure_Prediction "Wiki")

---

#### Machine Learning

1.1 **Ideas and Vocabulary**

* a machine learning device can generalize from real world observations into a “formal” model
* the model should reflect a concept or commonalities and not individual characteristics

* every learning scheme discards some aspects of reality to construct a model \(inductive bias\), this might also already happens on the level of feature extraction

* feature is a variable describing a specific aspect of real world observations

* training: phase of analyzing real world observations in a formalized representation to derive parameters and/or internal structure

* test phase: phase of model application to determine the reliability of statements \(predictions\) on instances not used for training

* unsupervised learning: concept learning, frequent item sets, clustering

* supervised learning: everything with labeled data which allows to make a prediction

1.2  **Data Preprocessing**

* Feature Extraction: Conversion of observation records into a formalized, computer-readable representation. Requires background knowledge from expert domains.
* Feature Selection: Removing values from instances, i.e. discard some features of a data set because these are: irrelevant, redundant, noisy/faulty. Possible benefits: improve efficiency and accuracy, prevent overfiing, save space. Strategies: unsupervised \(based on domain knowledge, random sampling\) and supervised \(Gini-index, information gain, use a learning scheme’s performance\)

1.3 **Machine Learning and Bioinformatics**

* the gain in speed to generate sequence data \(nucleotide sequences\) has clearly outpaced the speed of analysis and knowledge discovery
* current lab technology even cannot fill the gap between sequence and structure

1.4** Prevalence of ANN and SVM**

* they are capable to handle a huge number of attributes
* they are quite robust against uninformative features
* they implicitly adjust feature weights during the training phase
* you do not need to have an idea about the meaning of an input i.e. no background knowledge or understanding for feature selection or even stronger for feature generation necessary
* disadvantage: these methods are “black box” models, so inspec+ng the model does not really increase your knowledge/understanding
* probable disadvantage: performance depends on number of assumptions in the various processing steps
* probable disadvantage: consider the number of free parameters in respect to the number of available training instances 

1.5 **Redundancy Reduction**

Due to “experimental” reasons the sample represents only a special subset of the entities. The sampling of the “global” distribution is not fair. Possible solution is applying redundancy reduction to make the data a “fair” sample.

* CD-HIT: clusters sequences according to a user given threshold
* UniqueProt: creates representative, unbiased set of protein sequences based on HSSP values

1.6 **Performance Estimation**

* LOOCV: Leave on out cross validation: always one example is hold out for testing, the remaining for training
* N-fold cross validation, typically n=10:
  * partition the data in n partition
  * use n-1 partitions for training
  * use 1 partition for performance assessment
  * repeat with a different hold-out partition
  * average performance

1.7 **Drawbacks**

* Too many free parameters \(edges\) as well as overtraining leads to **overfiing** \(prediction model is biased towards the training examples\)
* Class imbalances. Solution: oversample minority class, downsample the majority class

#### Questions

** Question 1**: Can we predict secondary structure from protein sequence?

> **?**
>
> Not sure about the answer. I think, you still need 3D information \(from where we obtain structures\) for statistical information.
>
> If yes, then: Chou-Fasman, GORIII, ANN \(PHD\)

**Question 2:** What information do we obtain when predicting protein secondary structure? What features are predicted?

> Helix, sheet, coil formations

**Question 3: **How can we estimate the performance of secondary structure prediction methods?

> * Accuracy
> * Qx-measure \(Q3\)
> * Significance
> * Cross-validation

**Question 4**: Most often secondary structure predictions refers to the prediction of alpha helices, beta sheets and random coils. What other features of protein structure can be considered as secondary structure and be predicted?

> I asked Lothar about it and he said that this question doesn't have any meaning, even he could not answer it: only something like different types of turnes, but it's not very relevant

**Question 5: **List two secondary structure prediction methods.

> Prediction methods: Chou-Fasman, GORIII, ANN \(PHD\)

**Question 6: **Initially, prediction methods often focused on alpha-helices or underpredicted beta-sheets. What is the difficulty in recognizing beta-sheets from a window-based prediction method?

> b-sheet formation is not local



