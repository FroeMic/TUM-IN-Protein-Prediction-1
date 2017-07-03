## 3.1 Lecture Questions

> This section contains possible exam questions asked Professor Rost in the lectures he dedicated to answering student questions. They are **highly relevant, **because he will sample exam questions from this pool.

### Questions \(Thursday, 22nd June\)

**Question: **How can you choose the **e-value **for PSI-BLAST depending on the size of the dataset?

> ❓

**Question: **What is the regular process when you want to analyse a new sequence?

> ❓

**Question: **What is a structural domain? What is a functional domain?

> * structural domain: part of sequence with unique 3D structure
> * functional domain: part of sequence with unique function

### Questions \(Tuesday, 27th June\)

### Questions \(Thursday, 29th June\)

**Question: **With a matching _profile-profile_ comparison what can you say about the two families?

> The assumption is that matching profiles share a similar / same structure and function.

**Question: **When I build a profile of a famliy: Do they share the same structure? Should I verify that they do? How do i do that?

> The very assumption is that the proteins of one family share the same structure and function. When iteratively refining the profile with proteins retrieved by _profile-sequence_ of \_profile-profile \_comparison \(from the twilight- / midnight-zone\), it can make sense to double check the new proteins with secondary structure prediction to avoid adding false-positives.

**Question: **Cross-Validation: What is it? How does it work? Why do we need it?

> ❓

**Question: **What is the difference between a BLOSUM matrix and a PSSM \(Position Specific Substitution Matrix\)?

> ❓

**Question: **What is the most successful method to predict 3D structure?

> ❓

**Question: **What is homology modeling \(= comparative modeling\) and how does it work? What are the limitations of it?

> ❓

**Question: **How can you predict structure in the \[a\] daylight- \[b\] twilight- \[c\] midnight-zone?

> ❓

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
> ❓

**Question: **Say the 3D structure for **N **thousand proteins were known and they serve as input for a method predicting 1D structure. How can you define the value for \_sequence-unique** **\_that you have to apply to create an unbiased data set? Why do you need an unbiased dataset?

> ❓

**Question: **How do you compare proteins of different length?

> ❓

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

**Question: **Explain the concept between the notation of 1D, 2D, 3D structure. What is in the PDB? What does the DSSP give?

> ❓



