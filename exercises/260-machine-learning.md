## 2.6.0 Machine Learning 

###### 22.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170622_PP1_ml.pdf) \| [Wiki](https://i12r-studfilesrv.informatik.tu-muenchen.de/sose17/pp4cs1/index.php/Resources_for_Biological_Informations_/_Formats)

---

#### 1. Machine Learning

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

* the gain in speed to generate sequence data   \(nucleotide sequences\) has clearly outpaced the   speed of analysis and knowledge discovery
*  current lab technology even cannot fill the gap   between sequence and structure

1.4** Prevalence of ANN and SVM**

* they are capable to handle a huge number of   attributes
* they are quite robust against uninformative   features
* they implicitly adjust feature weights during the   training phase
* you do not need to have an idea about the   meaning of an input    i.e. no background knowledge or understanding   for feature selection or even stronger for feature   generation necessary
* disadvantage: these methods are “black box”   models, so inspec+ng the model does not really   increase your knowledge/understanding
* probable disadvantage: performance depends on number of assumptions in the various   processing steps
* probable disadvantage: consider the number of free parameters in   respect to the number of available training   instances 

1.5 **Redundancy Reduction**

Due to “experimental” reasons the sample represents only a special subset of the entities. The sampling of the “global” distribution is not fair. Possible solution is applying redundancy reduction to make the data a “fair” sample.

* CD-HIT: clusters sequences according to a user   given threshold
* UniqueProt: creates representative, unbiased   set of protein sequences based on HSSP values

1.6 **Performance Estimation**

* LOOCV: Leave on out cross validation:   always one example is hold out for testing, the   remaining for training
* N-fold cross validation, typically n=10  :
  - partition the data in n partition
  - use n-1 partitions for training
  - use 1 partition for performance assessment
  - repeat with a different hold-out partition
  - average performance

1.7 **Drawbacks**

* Too many free parameters \(edges\) as well   as overtraining leads to **overfiing** \(prediction model is biased towards
  the training examples\)
* Class imbalances. Solution: oversample minority class  , downsample the majority class

Questions



