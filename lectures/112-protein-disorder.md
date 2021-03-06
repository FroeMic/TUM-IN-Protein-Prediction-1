## 1.12 Protein Disorder

###### 27.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170627_disorder.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=AYidbIDB0Mo&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=11)

---

#### 1. Recap

#### 2. Intro

**Proteins are dynamic structures and thus they move.**

* Ligand Binding
* Catalysis
* Folding
* Allosteric Regulation \(?\)
* Libration \(?\)
* Sidechain rotation
* Vibration

![](/assets/Screen Shot 2017-07-06 at 17.40.31.png)**Natively unstructured regions:** a protein sequence that in solvent is unstructured \(2 time points will give different images\), but upon binding adopts a secondary structure \(induced fit\)

##### Features of Disorder

* Efficient binders \(larger interface / outreach\)
* Regulated through post-translation modifications
* Increasing complexity by structural plasticity
  * having a "key" for different locks \(bindings sites\) -&gt; bind to different subtrates
* Active only in **disordered version** \(large difference between on and off\)
* **Disorder is used for**
  * buffering
  * extending reach \(binding\)
  * extending reach \(signaling\)

##### Coupled binding an folding

* Fly casting: increase surface to 'reach out'
* Initial contacts weak and non-specific
* Folding upon approach of target

##### Types of natively unstructured regions

* unstructured 
* molten globule
* linked folded domains
* mostly folded local disorder

#### 3. Disordered Data

**Database:** DisProt - a database for disordered proteins  
**NORS:** no regulary structure  
**Loopy Disorder:** less than 5% helices / strand and more than 70 residues

* not found in PDB
* with a \(little\) relaxation long 'connecting' loops in protein were found
* about **10% of biomass** genome has such \(weird\) structures \(most of them in Eukaryotes\)
* on average these  NORS regions were **170 residues long**

**Problem:** Just looking for NORS does not predict shorter \(&lt; 70 residues\) disordered regions well

#### 4. Methods

##### 4.1 B-Value Prediction

**B-Value:** Backbone flexibility \(experimentally determined\)

_Can we predict them from sequence?_

* B-Values across PDB have to first be normalized \(different depending on family\)
  * B-Values in principle are conserved
* For ML the flexibility has to be projected on a simpler space \(flexible / not flexible\)
* Where to put the threshold?
  * 2 thresholds on the sides: Throw away 90% of your data. Not a good idea.
* * _Offtopic_: Putting the threshold around the peak, where the experimental error is the highest will consequently influence the model. \(never pick a peak!\)

**PROFbval:** Predict residue flexibility

* Classical PROF, with 2 output nodes: FLEXIBLE, RIGID
* **captures aspects of protein dynamics, NOT disorder directly**
* How are B-Values related to disorder?
  * No clear proportional correlation =\(

##### 4.2 NORS Region Prediction

_= distinguish unstructured from well structured loops_

**How can we detect shorter NORS regions, without lowering the threshold of 70 residues?**

**Idea:** Machine Learning

* Positive dataset = all NORS predictions \(&lt;70 residues\) in the entire proteomes
* Negative dataset = the whole PDB 
* Problem: Dataset is flawed
  * many considered 'false' are actually 'true'
  * many considered 'true' are actually 'false'

**How can a dataset with many mistakes be machine learned?**

* If the error is random \(white noise ≠ systematic error\),  a **consistent signal** is still strong enough to be picked up if the data set is big enough

##### 4.3 Contact Deprived Region Prediction

_Look at every pair of residues and look whether they are in contact -&gt; predict contacts._

_**Note:** 3D structure predictions from 1D structure is \(today\) still not solved. However, contact map prediction allows to distinguish between regions that are very constraint (e.g. binding sites) and those that are not._

Until now we did not assume to know 'what' disorder is. How do we then handle disorder 'experimentally'?

**Dunker Hypothesis:** Residues NOT visible in 3D structure share disorder. (You don't see it, because it moves to much)


##### 4.4 Meta-Disorder \(MD\)

Use a 'Meta-Predictor' which combines many methods.

* different methods focus on different aspects of protein disorder
* combining predictors substantially improves prediction

#### 5. Findings and Applications

#### Main Findings
* Specific contacts are important for disorder prediction
* Hub proteins (?) are abundant with unstructured loops
* different methods focus on different aspects of protein disorder
* combining predictors substantially improves prediction


**Eukaryotes dominate disorder **(x4 - x10): One reason could be that disorder is one stepping stone of complexity.
* Disorder allows proteins to have more (different) interaction partners and this intrinsically increases complexity.
* Bacteria in extreme conditions (heat, salt, ...) are much more similar to other bacteria in the same habitat regarding disorder than to their evolutionary closest homologs.

