## 1.3 Comparative Modelling

###### 18.05.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170518_cm1_exp3d.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=pGHwZE03omU&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=5)

---

* #### 1. Recap
* Profile-Sequence comparisons are more accurate than sequence-sequence aligments

* Profile-Profile alignments gain even more accuracy

**Question:** How do you build up a family \(profile\) of sequences?

> 1. Find proteins of similar structure with BLAST
> 2. Build PSSM
> 3. build up a set of pairwise alignments 
> 4. add those over a certain HSSP value to the family
> 5. Search with profile-sequence comparison for more distant family members and refine profile

* When building up a profile, start with a high threshold \(only very similar sequences are taken\), so the profile is not wrong from the beginnig

#### 2. Goal of structure prediction

_Sequence uniquely determines structure!_ ➡ Thus, from a sequence it should be possible to predict 3D structure and function

How would you assess prediction performance?

**CASP:** Critical Assessment of Structure Prediction

* Yearly event
* Submit predictions for structures, which will be experimentally predicted before a deadline
* Compare \(after release of experimental structures\) how the methods performed

**Current State**

* Only Homology Modeling is good
* No general prediction of 3D structure from sequence yet
* BUT: Important improvement in many fields

#### 3. Structure by Experiment

**Different Methods to determine 3D structure**

* 90% - X-Ray Crystallography 
* 09% - Nuclear Magnetic Resonance Spectroscopy \(NMR\)
* 01 % - Cryo Electron Microscope \(Cryo-EM\)

**X-Ray Crystallography **

1. **Grow Crystal:** Force the protein to grow a crystal
2. **Observe Diffraction Pattern**: Shoot x-rays onto crystal and observe the diffraction pattern
3. **Compute Electron Density Map**
4. **Fit observations to atomic model**

**NMR **

1. Protein has to be in similar solution as naturally
2. Massive Magnets required

**Cryo-EM **

* worse resolution than other methods
* cheaper than other methods
* _Pushing the boundaries of resolution of Cryo-EM is the future_

**Question:** Which methods to experimentally determine the structure of a protein exist? How much are they used?

> Fraction of proteins in the PDB by experimental method:
>
> * 90% - X-Ray Crystallography 
> * 09% - Nuclear Magnetic Resonance Spectroscopy \(NMR\)
> * 01 % - Electron Microscope \(EM\)

**Question:** How does X-Ray Crystallography Work

> 1. **Grow Crystal:** Force the protein to grow a crystal
> 2. **Observe Diffraction Pattern**: Shoot x-rays onto crystal and observe the diffraction pattern
> 3. **Compute Electron Density Map**
> 4. **Fit observations to atomic model**

##### Hydrogen Bond Formation

💡 **Idea:** Secondary structure is completely explained by hydrogen bond formation.![](/assets/Screen Shot 2017-07-03 at 13.05.28.png)**Helix:** Hydrogen-Bond between residue **i** and residue **i+4**, which stabilize the helix.  
**Sheet:** Two strands come together to form a sheet by forming hydrogen bonds between them

**Question:** How to get 1D secondary structure from 3D coordinates?

> Two methods where used to annotate 3D coordinates:
>
> 1\) DEFINE, based on geometry \(not used anymore\)  
> 2\) DSSP, based on hydrogen bond pattern \(coulomb energy\)

#### 4. Comparative Modeling \(=Homology Modeling\)

**Assumption:** Sequence uniquely determines structure and therefore, from similar sequence follows similar structure.

###### How can we use this to predict 3D structure?

**Target:** Protein to model  
**Template**: Protein to model from

1. **Identify Template:** Query the PDB for similar sequences to your **Target**
2. **Align Target / Template:** Select the best match as **Template **and assume the **Target** has the same structure
3. **Build Model**
4. **Assess Model** 
5. **Refine Model**

![](/assets/Screen Shot 2017-07-03 at 13.33.40.png)

**Question:** How does Homology Modeling \(Comparative Modeling\) work?

> **Target:** Protein to model  
> **Template**: Protein to model from
>
> 1. **Identify Template:** Query the PDB for similar sequences to your **Target**
> 2. **Align Target / Template:** Select the best match as **Template **and assume the **Target** has the same structure
> 3. **Build Model**
> 4. **Assess Model** 
> 5. **Refine Model**

**Question:** Which tradeoff does comparative modeling face? What are the limiting factors based on PSI \(Percentage Sequence Identity\)?

> **Tradeoff:** Accuracy vs Coverage
>
> Limiting factor in homology modeling:  
> 75% - 100%    -    Speed of Modeling  
> 50% -   75%    -    Quality of Model  
> 25% -   50%    -    Alignment Accuracy  
>   0% -   25%    -    Detection of Homology

#### 

#### 5. Comparative Modeling Methods

##### 5.1 MODELLER

**Summary: **lots of whistles and bells, downloadable, very accurate![](/assets/Screen Shot 2017-07-03 at 13.55.38.png)**Constraint Satisfaction:** use a set of objective functions to check whether the model is plausible

* $$C_{\alpha} - C_{\alpha}$$ distance
* Molecular dynamics
* Langevin dynamics
* Rigid bodies
* Rigid molecular dynamics
* ...

**Optimization Steps** \(run repeatedly\)

* explore different local minima

**Typical Errors**

* side chain packing
* misalignment
* wrong template

**Pick the right solution**: 

* based on DOPE score \(Discrete Optimized Protein Energy\)
  based on knowledge based pair potentials

##### 

##### 5.2 SWISS-Model

**Summary: **automated, increasingly comprehensive and flexible

**Underlying 'Philosophy'**

* fully automated
* for non-expert users / experimental biologists
* do less, make less mistakes

**Original**

1. alignment by BLAST / PSI-BLAST
2. copy to coordinates
3. end

**Today:** More complicated ...

