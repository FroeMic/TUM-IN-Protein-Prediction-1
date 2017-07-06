1.12 Protein Disoard

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
* For ML they flexibility has to be projected on a simpler space \(flexible / not flexible\)
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



##### 4.3 Contact Deprived Region Prediction

##### 4.4 Meta-Disorder \(MD\)

#### 5. Findings and Applications



