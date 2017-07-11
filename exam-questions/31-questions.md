## 3.1 Lecture Questions

> This section contains possible exam questions asked Professor Rost in the lectures he dedicated to answering student questions. They are **highly relevant, **because he will sample exam questions from this pool.

### Questions \(Thursday, 22nd June\)

**Question: **How can you choose the **e-value **for PSI-BLAST depending on the size of the dataset?

> E-value indicates significance of alignment/ hits returned by chance when searhing through DB. It depends on the size of dataset and length of query. So higher e-values from large DB aren't always bad \(and opposite: smaller e-values from small sample space isn't always good\).

**Question: **You want to develop a new method to predict e-values, how do you prepare your data?

> you need to look at how e-value changes through iteration, width of background distribution, height of score

**Question: **What is the regular process when you want to analyse a new sequence?

> ❓
>
> Go to DB and search your sequence to find out whether homologs of this protein are already available, and if they are, what is known about them.
>
> If we didn't retrieve any significant hits, try to search for motifs, patterns.

**Question: **What is a structural domain? What is a functional domain and How can we deal with the fact that they can be in different places?

> * structural domain: part of sequence with unique 3D structure
> * functional domain: part of sequence with unique function
> * use local alignment

### Questions \(Tuesday, 27th June\)

**Question: **How do we predict proteins?

> **?**
>
> * use DB to search for homologs
> * use Machine learning and other methods for secondary structure prediction
>
> * use Comparative modelling for 3D structure prediction

**Question: **Why would someone give you a sequence?

> Amount of newly discovored sequences constantly increses. And even for known sequences we still can refine information that we have about them.

**Question: **How do you run a sequence against the DB?

> * Blast search \(uses indexing technique, scoring matrix and dynamic programming to find short similar segments\)
> * Psi-Blast search \(at first it uses Blast search, creates profile \(PSSM\) from highest scoring hits and uses it to replace substitution matrix in a subsequent Blast search, this process can be repeated many times to refine profile\)

**Question: **How do you build a family?

> Use non-redundant database. Set a threshold for E-value. Perform similarity search of all the proteins against eash other using Blast. Proceed results i.e. set thresholds for including proteins in family \(similarity, sequence length\). For each family align proteins using ClustaW.

**Question: **Pairwise/multiline alignment: what can we acheive, what is the risk?

> Multiple alignment can be used to find pattern characteristics of specific protein families, build phylogenetic trees, detect homology between new sequence and existing families, help in predicting secondary structure of new sequence.
>
> Sequence alignment can fhelp in: finding conserved regions between the 2 sequences, similarity searches in DB.
>
> In case of Multiple alignment there is a risk of pollution, any errors in the initial alignments cannot be corrected later as new information from other sequences is added.

**Question: **What is the difference between pairwise and multiple alignment?

> Pairwise alignment compares 2 sequences, multiple - 3 and more. \(Also look previous question\)

**Question: **Can we predict something we have not observed?

> When we predict features we can try to find somthing that people "want" to see.

**Question: **Sliding windows introduce information from the sequence environment. Why do we need convolutional network on top of that? Why do we need anything else on top? _\(not sure about correctness of question\)_

> It gives us ability to detect motifs whenever it's in sequence window. It exploits spatially local correlation.

**Question: **How do we prepare data to predict B-value? _\(not sure about correctness of question\)_

> 1. B-Values in principle are conserved. Thus the B-Values for proteins across the PDB have to first be normalised \(different depending on family\)
> 2. Thresholding. In order to map the continuous space to outputs \(rigid / flexible\), thresholds have to be set \(not at the peak of the distribution, since the experimental error is the biggest there.

### Questions \(Thursday, 29th June\)

**Question: **With a matching _profile-profile_ comparison what can you say about the two families?

> The assumption is that matching profiles share a similar / same structure and function.

**Question: **When I build a profile of a famliy: Do they share the same structure? Should I verify that they do? How do i do that?

> The very assumption is that the proteins of one family share the same structure and function. When iteratively refining the profile with proteins retrieved by _profile-sequence_ of \_profile-profile \_comparison \(from the twilight- / midnight-zone\), it can make sense to double check the new proteins with secondary structure prediction to avoid adding false-positives.

**Question: **Cross-Validation: What is it? How does it work? Why do we need it?

> Is an validation technique for assessing how the results of a statistical analysis will generalize to an independent data set. We need it to to estimate how accurately a predictive model will work in practice
>
> N-fold cross-validation: Partion data in 'n' folds. Use 'n-1' for training and 1 for performance assessment. Repeat with different hold out partitions. Average perfomance.

**Question: **What is the difference between a BLOSUM matrix and a PSSM \(Position Specific Substitution Matrix\)?

> In case of PSSM  a.a. substitution scores are given separately for each position in a protein multiple sequence alignment. And in Blosum we have substitution scores for all possible substitution pairs \(210 in total\) of 20 standard a.a.

**Question: **What is the most successful method to predict 3D structure?

> comparative modelling

**Question: **What is homology modeling \(= comparative modeling\) and how does it work? What are the limitations of it?

> Allign sequence with proteins in PDB and set a threshold. Introduce gaps as loops.
>
> Limitation - no similarities found \(templates are unavailable or fragmentary\), matching right residues \(errors in sequence alignment produce errors in the homology model\)

**Question: **How can you predict structure in the \[a\] daylight- \[b\] twilight- \[c\] midnight-zone?

> While using sequence-sequence, sequence-profile and profile-profile alignment respectively.

**Question: **What is the assumption behind all alignment methods that is incorrect and nevertheless seems to work? Give a method that aligns 2 proteins without that assumption.

> The assumption is that the alignment of the residue at position **i **is independent of the **i+x**. \(In short: alignment i and i+1 are independent\).  
> The only method that does not rely on this assumption is the **Genetic Algorithm** \(e.g. T-Coffee\)

**Question: **Why do we have so few experimentally confirmed structures in the PDB?

> ca. 85 million proteins are known, but only about 120 000 are in the PDB.
>
> Sequencing technology has improved and become a lot cheaper and hence many more proteins were discovered. While there were improvements in 3D structure determination, it still costs at least 100 000 euros to experimentally determine the 3D structure of a protein. It is expected that this divide will further increase.

**Question: **Why do we need redundancy reduction for machine learning?

> The training data for the ML model should be representative for the problem for which it should predict.
>
> Half of known structures in DB have 100% sequence similarity

**Question: **Say the 3D structure for **N **thousand proteins were known and they serve as input for a method predicting 1D structure. How can you define the value for \_sequence-unique** **\_that you have to apply to create an unbiased data set? Why do you need an unbiased dataset?

> ❓
>
> Using RMSD and putting a threshold
>
> We need an unbiased dataset in order to assess perfomance of 3D to 1D prediction.

**Question: **How do you compare proteins of different length?

> ❓
>
> By using local alignment

**Question: **What is the significance in using information from protein families \(also inferred as evolutionary information\) as input to the ML device predicting 3D structure?

> * It is additional information for the ML device, which is clearly relevant for the structure
> * the profile is a record with information about the 3D reality of the protein
>
> ❓

**Question: **How can I use 1D information to get a 3D structure? What can you do with a 1D structure?

> It is impossible to reconstruct a full 3D structure from 1D information. 1D structure can be used for
>
> * optimizing a profile
> * predict whether a protein is soluble
> * predict whether a protein is a transmembrane protein
> * input for further secondary structure prediction
> * ❓

**Question: **What is a 2D contact map \(distance map\)? How can it be obtained?

> ❓
>
> Shows distsnce between all possible a.a. pairs.
>
> By using 3D structure and distance functions \(i.e. Voronoi contacts\)

**Question: **Explain the concept between the notation of 1D, 2D, 3D structure. What is in the PDB? What does the DSSP give?

> **?**
>
> 1D - secondary structure
>
> 2D - contact map
>
> 3D - tertiary structure, 3D shape of protein
>
> In PDB there is only 3D structure
>
> DSSP assigns secondary structure according to hydrogen-bond pattern

### Questions \(Tuesday, 4th July\)

**Question:** Why do we need separate methods to predict secondary structure for membrane and water-soluble / non-membrane proteins? What is needer for membrane prediction beyond secondary structure?

> Methods trained to predict secondary structure in soluble environment fail for membrane proteins \(empirical observation\). Reason for this is that the environment \(the membrane\) is very different.
>
> Number of alpha - helixes is important, as it defines function of membrane protein. Position of alpha-helixes, topology.
>
> ❓

**Question:** What is the principle difference between PSI-BLAST and CLUSTALW \(or any other multiple sequence alignment method\)?

> The differ in the way the background statistics are compiled. BLAST is so fast because it compiles the background statistics only once. CLUSTALW on the other hand uses random sampling.❓
>
> Optimization Criteria is different:
>
> * BLAST: Alignment
> * CLUSTALW:  Optimize family alignment
>
> ❓

**Question:**  How do you measure the similarity between a profile \(PSSM\) and a sequence?

> You calculate the PSSM score.
>
> // Not explicitly  noted down by him. Generally, understand how Profile-Sequence alignment with a PSSM works.

**Question:** In the 1st iteration of PSI-BLAST finds the most low hanging fruits through pairwise comparison. \[a\] What does it do in the 2nd iteration? \[b\] Why can this work better? \[c\] What could happen that makes the 3rd iteration not find more more hits than the 2nd one \(for all n=1=…N\)?  \[d\] Say n+1 finds many more hits than n:  everything ok?

> \[a\] It uses the compiled PSSM to run a profile-sequence comparison against the database.
>
> \[b\] Because the PSSM contains information about the entire family, the initial query sequence belongs to. Within the PSSM there is information about the evolutionary preserved \(and thus for structure / function important\) segments/residues for this specific family.
>
> \[c\] This either happens if the profile converged, hence I found all the proteins belonging to the family. If this happens very early e.g n=2, it indicates that I could not find enough proteins to build up a profile \(family is too small\).
>
> \[d\] It could have happened that the profile was messed up by proteins, which are not part of the family in an earlier run. The new PSSM does not discriminate well enough between proteins.

**Question:** How is the **e-value** for PSI-BLAST, FASTA calculated.

> * PSI-BLAST
>
>   * … ?
>   * e-value changes over iterations

**Question:** What might per-residue  scores poorly reflect the performance of transmembrane prediction? Invent an alternative method to score TMH prediction methods.

> * For most membrane proteins, most residues are NOT in the membrane. 
> * It is not really what I want to predict. I want to predict the specific TMH. How many TMH do I have?  At which position are they? Which topology does the protein have?

**Question:**  Method A is published to predict solvent accessibility at Q2=61%, Method B in another publication claims to achieve Q2=63%. What do you have to check to ascertain that methods B is really a better methods? \(Address the terms significance \(statistical, scientific\) in your response\)

> * Use the same way of computing Q2?
> * Do the use the same data?
> * Which data was used to train the method? Best, test both methods on proteins  that where released after the methods were published.
> * Is there a difference between the methods beyond the standard error? Is the difference in accuracy statistically significant?
> * Does the +2% help me to get better scientific results / insights? Is there an advantage in scientific terms? Is it better than random?

**Question:** What features can be used to predict secondary structure from sequence? Argue why?

> * The PSSM is the most important features?
> * … \(many more\) ❓

**Question:** What is the most accurate way to predict protein 3D structure \(explain the idea behind the method\) ? Why does this methods hardly work for membrane proteins and even less well for disorder proteins?

* > Homology Modeling  
  > … ❓

**Question:** UniProt currently holds about 85 Million proteins sequences: Do we have any idea about the structure of any of those? Roughly for how many? Do we have any idea how many of the 85Million are membrane / disorder?

> * Yes, for those in the PDB \(about 120k\)
> * By membrane prediction methods, we can predict which proteins are membrane proteins. So we can predict the number of membrane / disorder proteins under consideration of prediction accuracy
> * For the human proteon, it is estimated that about 25% are membrane proteins.

**Question:** You want to use a regular neural network \(input/hidden/output\) too solve a certain prediction model. \(e.g. predict disordered regions\). How can you find how many hidden units you need? How what the best input is? How to best code the output \(here disorder\)?

> * empirically - you need to try it
>   * Start with the output unit? What do you want to get out?
> * output: reliability, …
> * input: try out what do pull in? What has worked for others?
> * hidden: defined by the complexity of the problem and the number of samples
>
> ❓

**Question:** You want to develop a method to predict secondary structure in 3 states \(HEL\). How can you use DSSP to convert the 3D structure in the PDB to HEL.  What do you have to watch? Can you use the entire PDB? Once you have N proteins in you dataset: how can you assess prediction performance? \(How to measure ‘right’, name a few score that are relevant, how to measure statistical significance, how to measure scientific significance\)

> 1. Redundancy reduced dataset, "remove" all proteins in comparative modeling range.
> 2. "Remove" fraction of dataset for later blind testing \(no overlap with training set allowed\)
> 3. Use blind test to assess perfomance
>    1. Q3 = number of correctly predicted residues / total number of residues
>    2. Number of correctly predicted H, E, L
> 4. Statistical significance 
>    1. Determine average Qx - value on your dataset
>    2. Calculate the standard deviation \(sigma\)
>    3. Calculate standard error \(sigma/sqrt\(N\)\)
>    4. Compare the new method to other method \(baseline\) performance + standard error
> 5. Scientific significance
>    1. Does the perfomance increase helps to push new scientific findings

**Question:** TMH prediction: How can you predict the direction of a helix? What assumption does comparative modelling make? Why do proteins always have to adopt the same 3D structure? Do different organisms use different proteins? How much does it cost \(time/money\) to experimentally determine the 3D structure of an average protein?

> 1. Positive-inside rule
> 2. Similar sequence -&gt; similar struction
> 3. No? \(there are similar proteins among different animals\)
>
> X-ray: ~1 year, 100 000 euro \(can go up to million in certain cases\). 
> NMR crystallography: more time consuming and more expensive \(due to spectrometer costs and isotope labelling\) than X-ray crystallography. A standard 600 MHz NMR costs roughly $800,000, but the 900 MHz sells for about $5 million.

**Question:** How would you define life? How are proteins crucial to maintain it?

> Descriptive definitions of life:
>
> * Homeostatis \(regulation of internal environment to maintain constant state\)
> * Organization \(Unit: Cells\)
> * Metabolism
> * Growth
> * Adaptation
> * Response to stimuli
> * Reproduction
>
> functions of proteins:
>
> * Defense \(e.g. antibodies\)
> * Structure \(e.g. collagen\)
> * Enzymes \(metabolism, catabolism\)
> * Communication / Signaling \(e.g. insulin\)
> * Ligand binding / Transport \(e.g. hemoglobin\)
> * Storage \(e.g. ferritin\)

**Question:** Why do we need membranes around cells? What are they made of? Why do proteins pass through membranes?

> It physically separates the intracellular components from the extracellular environment and provides shape of the cell. Also membrane is a dynamic structure \(cell can grow and shrink\).
>
> The cell membrane is a bilayer of phospholipids.The phospholipid bilayer is hydrophilic on the outside and hydrophobic on the inside. 
>
> Transmembrane proteins are anchored into the bilayer by their nonpolar segments.TMP can move laterally \(sideways\) in the membrane.

### Questions \(Thursday, 6th July\)

**Question:** What does the reliability of variants tell us about the severity of effect and why?

> ❓

### Questions \(Tuesday, 11th July\)

**Question:** State one example in which the replacement of graphs by hypergraphs reduces the information-loss when modeling cellular and/or physical systems.

> When modeling protein interactions, some functions are the result of protein complexes with more than 2 proteins. A hypergraph can have edges between an arbitray number of vertices, whereas a regular graph can only connect 2 vertices with and edge.
> If we modeled the interaction of 3 proteins with a regular graph, we would 
> [1] either connect all nodes pairwise, losing the information whether they do (or do not) interact pairwise as well
> [2] don't model the 3-way interaction at all (loosing exactly this information)
