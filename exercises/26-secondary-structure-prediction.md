## 2.6 Secondary Structure Prediction

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







