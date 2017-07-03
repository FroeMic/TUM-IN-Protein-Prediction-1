## 3.1 Lecture Questions

> This section contains possible exam questions asked Professor Rost in the lectures he dedicated to answering student questions. They are **highly relevant, **because he will sample exam questions from this pool.

### Questions \(Thursday, 22nd June\)

**Question: **How can you choose the **e-value **for PSI-BLAST depending on the size of the dataset?

> E-value indicates significance of alignment/ hits returned by chance when searhing through DB. It depends on the size of dataset and length of query. So higher e-values from large DB aren't always bad \(and opposite: smaller e-values from small sample space isn't always good\).

**Question: **You want to develop a new method to predict e-values, how do you prepare your data?

> **?**
>
> Maybe to consider length of sequences, data base size, redundancy of data

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

> **?**
>
> Training set: non-redundant set of high resolution protein structures. Network is trained on properties that can be obtained from primaary a.a. sequence: secondary structures and solvent accessibility. We can also use evolutionary profile and global information about sequence.
>
> \(There is an answer in the last video lecture, which is not uploaded yet\)

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

> The assumption is that the alignment of the residue at position **i **is independent of the **i+1**. \(Short alignment i and i+1 are independent\).
>
> Method w/o that - Genetic algorithm that operates on segments

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



