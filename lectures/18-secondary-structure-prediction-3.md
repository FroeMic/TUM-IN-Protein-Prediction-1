## 1.8 Secondary Structure Prediction 3

###### 08.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/cb1e_20170601_sec2.pdf) \| [Lecture Recording](https://www.youtube.com/watch?v=BmOE3X6Qh98&list=PLg46T0OlBIJ9abbsmUL-ux24DCpoUlC1J&index=7)

---

#### 1. Recap

**Goal of Structure Prediction:** Predict the 3D structure and function from an input sequence.

**Cell:** The density of a cell is like solid state, but proteins are still surounded by water

**Relation of Proteins:** We can find out about the relation of proteins by comparing their sequence

* direct sequence-sequence comparison only in the daylight-zone
* building up profiles means to 'pick up the implicit evolutionary signal'

**Question:** Which ways of comparing proteins are there? Why do we need

> * Dynamic Programming \(Brute Force\)
> * Hashing \(e.g. BLAST\)

**Question:** Why are fast search algorithms such as BLAST needed?

> Comparing sequences of length $$n$$ residues is in $$O(n^2)$$. For comparing a single pair this is still fine, but comparing one \(newly found\) protein against all known proteins in the PDB \(about 120 000\) is impossible. Thus we need 'shortcuts' such as BLAST to speed up the search.

**Question:** What is the normal approach when you find / analyse a newly found protein?

> ❓  
> 1\) Sequence the new protein \(if not done yet\)  
> 2\) Run BLAST against the PDB  
> 3\) Run Dynamic Programming against the results from BLAST

**Question:** In terms of CPU, is sequence-sequence as fast as sequence-profile?

> ❓

**Question:** How can it be that even with only 40% sequence identity we assume / observe similar structure?

> The changes in sequences we observe are not random, but follow underlying evolutionary rules. Changes, which affected the structure and thus the function of a protein are simply not likely to survive and thus we do not observe them. Changes, which did not influence the structure / function however, did survive.

**Question:** Why is protein sequence changing? Why are we mutating?

> * Replication Errors \(point mutations\)
> * Radiation
> * Viruses

**Question:** How much do any two unrelated typical humans differ on average?

> On average every pair of humans would differ in one amino acid per protein. \(Though, changes cluster\)

**Question:** In a structure to structure network, which additional information could be used to improve the prediction?

> * E.g. redundant information about the sequence, e.g. parts of it.
> * length of  protein
> * Is the sliding window at the end / mid / start of the protein?

**Question:** When training a neural network, how do you choose the next training sample from your test set? Why so?

> Randomly, to avoid correlations

#### 2. 3rd Generation Secondary Structure Prediction

**Critical Question:** How to improve beyond $$60\% + \epsilon$$ accuracy?

**Evolution improves prediction**: An **evolutionary profile** averaged built up over several species implicitly captures the history of an individual protein.

##### PHD: Neural Network and Evolutionary Information

* Build up the family \(profile\) for the protein and add it to the input of the network
* Each amino acid in the input now has a probability on how often it occurs in the family

![](/assets/Screen Shot 2017-07-02 at 19.19.34.png)**Additional Input for PHDSec network**

* family \(profile\)
* percentage of each amino acid in protein
* length of protein
* distance: center, N-term
* distance: center, C-term

**Jury decision improve accuracy:** All of these input features are fed to different Networks, resulting in many independent predictors \(**Jury**\). All of these networks add their own 'white noise' to the prediction. The average over all the predictors is better than every single one.

The final accuracy \(on average\) of ProfSec is about **72%**. 

**Prediction of correctly predicted residues: **In additional, **ProfSec can give an estimation on the strength of the prediction** for each protein. \(By counting the 'stars'\)![](/assets/Screen Shot 2017-07-02 at 20.19.46.png)

**Question:** How does ProfSec overcome the 60% accuracy hurdle in secondary structure prediction?

> ProfSec uses evolutionary information - the family of the protein - as additional input. Furthermore, other relevant input data \(e.g length of protein, distribution of amino acids, ...\) are used to build up several different networks that independently predict the secondary structure. Together this jury of networks achieves a more accurate prediction than they would on their own.

**Question:** How would you build up a family for a protein?

> 1. Search the PDB for proteins in comparative modeling range. \(Assumption: same sequence, same 3D structure, same secondary structure\)
> 2. Use profile to search in twilight-zone for potential proteins of that family \(possibly verify whether the found protein is plausible to have similar 3D structure\) and add to family \(recompute profile\)

**Question:** How do you get from a sequence to a secondary structure prediction with PHD?

> 1. Use BLAST to find potentially similar proteins in sequence data bank
> 2. For the resulting proteins calculate the sequence identity \(homology\) with dynamic programming
> 3. Filter all proteins, which are below a threshold of sequence identity \(only take those "over the curve"\)
> 4. Extract the profile by aligning the remaining proteins
> 5. Predict the secondary structure with the sequence and its family as input

**Question:** Which accuracy does ProfSec achieve on average? What are additional advantages of other secondary structure prediction methods?

> ProfSec achieves a Q3 accuracy of about 72% on average. Additionally it can also predict the strength of the prediction.



