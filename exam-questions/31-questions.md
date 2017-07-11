## 3.1 Lecture Questions

> This section contains possible exam questions asked Professor Rost in the lectures he dedicated to answering student questions. They are **highly relevant, **because he will sample exam questions from this pool.

### Questions \(Thursday, 22nd June\)

**Question:** How can you choose the **e-value **for PSI-BLAST depending on the size of the dataset?

> - The E-value indicates significance of alignment/ hits returned by chance when searhing through DB. 
> - It depends on the size of dataset and length of query. 
>
> So higher e-values from large DB aren't always bad \(and opposite: smaller e-values from small sample space isn't always good\). (?)
 
**Question:** You want to develop a new method to predict e-values, how do you prepare your data?

> You need to look at how the e-value changes through iterations, width of background distribution, height of score

**Question:** What is the regular process when you want to analyse a new sequence?

> [Note: A question such as this would need more information I think. What do I want to know about the new sequence?]
>
> 1. Search UniProt whether the sequence is known. If so, also check the PDB - maybe there is already a 3D structure.
> 2. Run BLAST against the PDB to find homologs. If there are suitable hits, homology modeling might be possible. In such a case 'Modeller' or 'Swiss-Model' could be used to predict a 3D structure for the protein.
> (In addition, informed estimations about the function of the protein can be made based on the homologs found.)
> 3. If Homology Modeling is not possible, there is still more to uncover about the protein. First, one could search for motifs and patterns. Second, PSI-BLAST could be used to builda profile of the family, thereby uncovering more distant relatives and conserved regions.
> 4. To further analyse the sequence secondary structure and/or membrane predictions (is it a membrane protein?) can be of used.
> 
> Which analysis method we choose, ultimately depends on, what we want to find out about the discovered sequence.

**Question:** What is a structural domain? What is a functional domain and How can we deal with the fact that they can be in different places?

> * structural domain: part of sequence with unique 3D structure
> * functional domain: part of sequence with unique function
> * use local alignment

### Questions \(Tuesday, 27th June\)

**Question:** How do we predict proteins?

> [Note: Too general question for the exam...]
>
> [1] Predict Function:
> * We cannot predict function directly. The general assumption is that from same 3D structure we can assume same function.
>
> [2] Predict 3D Structure
> * The only reliable way to predict 3D structure is **homology modeling**. 
>     * Find homologs with known 3D structure by sequence identity (assumption: high sequence identity -> similar 3D structure)
>     * Use homology modeling (Modeller, Swiss-Model): Apply known 3D structure of homolog to query sequence and refine constraints
>     
> [3] Predict Secondary Structure
> * Use algorithms (GOR III, ProfSec) to predict secondary structure. Possibly as input for further analysis.
> 
> [4] Predict Membrane Proteins
> * Predict different features about Trans-Membrane Proteins.
>     * Is a protein a membrane protein (check e.g. hydrophobicity)
>     * Are there Trans-Membrane Helices (TMH) or Beta-Barrels? At which postion are they?
>     * In which direction is the membrane crossed? (Toplogy, Inside-Positive Rule)

**Question:** Why would someone give you a sequence?

> The amount of newly discovered sequences constantly increases (sequencing is very cheap and fast)
> And even for known sequences we still can refine information that we have about them

**Question:** How do you run a sequence against the DB?

> * BLAST search \(uses indexing technique, scoring matrix and dynamic programming to find short similar segments\)
> * PSI-BLAST search \(at first it uses Blast search, creates profile \(PSSM\) from highest scoring hits and uses it to replace substitution matrix in a subsequent searches, this process can be repeated many times to refine profile\)

**Question:** How do you build a family?

> 1. Run BLAST against the entire database (e.g. UniProt) to find proteins with high sequence similarity. From these 'homologs' found, we can assume an evolutionary relationship based on their high PSI. (Important! Get the statistics right and only add proteins which are from the Daylight Zone)
> 2. Calculate a PSSM with the homologs found. (= profile) This reveals conserved residues / regions.
> 3. Use this PSSM to perform a Profile-Sequence search against the database to discover more distant family members.
> 4. Recalculate the PSSM to refine the profile with the newly found proteins. Perform another round of Profile-Sequence search against the Database, if no stop-criterion was reached.

**Question:** Pairwise/Multiple alignment: what can we achieve, what is the risk?

> Pairwise Alignment aligns exactly 2 sequences. This is necessary to e.g. further compute 3D similarity or make assumptions about evolutionary and functional relatedness. It is important to always consider the background distribution, length of sequence, size of database. (= How probable is it that such an alignment score happened by chance?
>
> Multiple Sequence Aligment tries to align more than 2 sequences. This is computationally infeasable for more than 6 proteins, so 'shortcuts' are needed. (e.g. CLUSTAL, BLAST). Multiple sequence alignments help to uncover conserved evolutionary information about a protein family, which in turn can help to find more distant relatives (in terms of sequence identity).
> (In case of Multiple alignment there is a risk of pollution, any errors in the initial alignments cannot be corrected later as new information from other sequences is added.)

**Question:** What is the difference between pairwise and multiple alignment?

> Pairwise alignment compares 2 sequences, multiple aligment- 3 and more. \(Also look previous question\)

**Question:** Can we predict something we have not observed?

> When we predict features we can try to find somthing that people "want" to see.

**Question:** Sliding windows introduce information from the sequence environment around a residue. Why do we need a second neural network on top of that? Why do we need anything else on top? 

> The second (independently trained) structure-to-structure network helps to improve prediction performance for helices and sheet by solving the 'short segment' problem.
> It gives us ability to detect motifs whenever it's in sequence window. It exploits spatially local correlation.

**Question:** How do we prepare data to predict B-value? _\(not sure about correctness of question\)_

> 1. B-Values in principle are conserved. Thus the B-Values for proteins across the PDB have to first be normalised \(differently depending on family\)
> 2. Thresholding. In order to map the continuous space to outputs \(rigid / flexible\), thresholds have to be set \(not at the peak of the distribution, since the experimental error is the biggest there.

### Questions \(Thursday, 29th June\)

**Question:** With a matching _profile-profile_ comparison what can you say about the two families?

> The assumption is that matching profiles share a similar / same structure and function.
> (?) Also evolutionary connection?

**Question:** When I build a profile of a famliy: Do they share the same structure? Should I verify that they do? How do I do that?

> * The very assumption is that the proteins of one family share the same structure and function.
> * When iteratively refining the profile with proteins retrieved by _profile-sequence_ of _profile-profile_ comparison \(from the twilight- / midnight-zone\), it can make sense to double check the new proteins with secondary structure prediction to avoid adding false-positives to the family.

**Question:** Cross-Validation: What is it? How does it work? Why do we need it?

> Is an validation technique for assessing how the results of a statistical analysis will generalize to an independent data set. We need it to to estimate how accurately a predictive model will work in practice
>
> N-fold cross-validation: Partion data in 'n' folds. Use 'n-1' for training and 1 for performance assessment. Repeat with different hold out partitions. Average perfomance.

**Question:** What is the difference between a BLOSUM matrix and a PSSM \(Position Specific Substitution Matrix\)?

> * In case of a PSSM  amino acide substitution scores are given separately for each position in a protein sequence. 
> * In BLOSUM62 we have substitution scores for all possible substitution pairs \(210 in total\) of the 20 standard amino acids. (NOT specific to their position in a sequence)

**Question:** What is the most successful method to predict 3D structure?

> Homlogy (Comparative) Modeling.

**Question:** What is homology modeling \(= comparative modeling\) and how does it work? What are the limitations of it?

> 1. Align sequence with proteins in PDB and set a threshold. Introduce gaps as loops.
>
> Limitation - no similarities found \(templates are unavailable or fragmentary\), matching right residues \(errors in sequence alignment produce errors in the homology model\)

**Question:** How can you predict structure in the \[a\] daylight- \[b\] twilight- \[c\] midnight-zone?

> By using \[a\] sequence-sequence, \[b\] sequence-profile and \[c\] profile-profile alignment respectively.

**Question:** What is the assumption behind all alignment methods that is incorrect and nevertheless seems to work? Give a method that aligns 2 proteins without that assumption.

> The assumption is that the alignment of the residue at position **i** is independent of the residue **i+x**. \(In short: alignment i and i+1 are independent\).  
> The only method that does not rely on this assumption is the **Genetic Algorithm** \(e.g. T-Coffee\)

**Question:** Why do we have so few experimentally confirmed structures in the PDB?

> ca. 85 million proteins are known (UniProt), but only the 3D structure of about 120 000 are in the PDB.
>
> * Sequencing technology has improved and become a lot cheaper and faster. Hence, many more proteins were discovered. 
> * While there were improvements in 3D structure determination, it still costs at least 100 000 euros to experimentally determine the 3D structure of a protein. 
> * It is expected that this divide will further increase.

**Question:** Why do we need to perform redundancy reduction on our dataset befor training our machine learning model?

> The training data for the ML model should be representative for the problem for which it should predict.
>
> * The known 3D structures in the PDB largely share a high sequence similarity (because of different resolutions, competing groups, different research goals, ...), are thus applicable for homology modeling and not representative for the dataset we want to predict for in the future.
> * Removing the sequences in homology modeling range (redundancy reduction) creates an unbiased dataset.

**Question:** Say the 3D structure for **N **thousand proteins were known and they serve as input for a method predicting 1D structure. How can you define the value for \_sequence-unique** **\_that you have to apply to create an unbiased data set? Why do you need an unbiased dataset?

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
