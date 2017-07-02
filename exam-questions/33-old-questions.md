## 3.3 Question Catalogue

> This section contains possible exam questions sourced from students of previous Protein Prediction I lectures and the lecture recordings.

### 3.3.1 Exam Structure: 2016ST

> We where able to obtain last years exam structure. Let's try to answer all of the concrete questions :-\)

_Part 1 is mandatory, for the rest choose 3 out of 4._

##### **1. Multiple Choice \(5 questions, 10 points\)**

* Secondary Structure
* RMSD - Protein Similarity
* Hydrogen Bonds \(⍺-helix, β-sheets, long/short bonds\)
* 100% sequence identity =&gt; same structure? \(PIDE\)
* Can modern prediction methods correctly predict structure in the midnight zone?
* About "Cryo-Microscope" ❓
* About "X-Rays" ❓

##### 2**. Sequence Alignment \(10 points\)**

* Explain each of the following alignment techniques and provide one method for each

  * Sequence - Sequence
  * Sequence - Profile
  * Profile - Profile

* General scoring BLOSUM62 matrix vs. PSSM

* Why is the sequence information valuable?

* How BLAST speed up pairwise alignments?

* Global vs Local alignment

##### 3**. Sequence Structure \(10 points\)**

* What data is needed to predict the structure with ML?
* Which tools and db you will use?
* How to prepare data for ML
* Which 2-3 features will help to predict?
* Would you apply method to all protein \(query\)?
* Which measure would you use to evaluate your method?

##### 4**. Protein Structure \(10 points\)**

* Why it is important to know 3D structure?
* Why is it so hard to compare 3D structure?
* Most successful ML algorithm for predicting structure, steps
* Method for experimental structure determination. Short explanation. How many structures are experimentally known?

##### 5**. Machine Learning \(10 points\)**

* General definition of Machine Learning
* Cross validation
* What is ‘feature’?
* ETP explain, example
* Name and describe one ML method
* Name and describe "sequence" in context of PP
* Discuss how to predict Protein Structure from amino-acid sequence using ML
* Q2: which is better, how to prove your’s is better, which value you will publish? \(❓What is Q2\)

### 3.3.2 Lecture 1: Introduction Bioinformatics

**Question:**What is common to life?

> DNA, Protein, RNA

**Question:** How many bacteria do we care around?

> About 2 kilos. Humans carry around more bacterial DNA than human DNA.

**Question:** Which elements make up life?

> * 65.0 % - O, Oxygen
> * 18.6 % - C, Carbon
> * 9.7 % - H, Hydrogen
> * 3.2 % - N, Nitrogen
> * 1.8 % - Ca, Calcium
> * 1.0 % - P, Phosphorus

**Question:** What is life? Can you define it?

> There is no holistic definition of life: Descriptive definitions of life are
>
> * Homeostatis \(regulation of internal environment to maintain constant state\)
> * Organization \(Unit: Cells\)
> * Metabolism
> * Growth
> * Adaptation
> * Response to stimuli
> * Reproduction

**Question:** Are viruses life?

> Strictly speaking NO. Viruses on their own cannot replicate and thus are not alive. However, one could say that viruses are alive / represent life once they infected a cell and replicate.

**Question:** What do bacteria have in common?

> Single Cells

**Question:** What are the differences between prokaryotic and eukaryotic cells?

> **Prokaryotic Cells:** mainly found in bacteria and archaea, usually unicellular, no nucleus, no cell organelles  
> **Eukaryotic Cells:** Found in animals and plants, usually multicellular, have nucleus, have cell organelles

**Question:** How can the density of a cell be described?

> The state inside a cell is almost solid. We can think of a cell similar to a Christmas day on Time Square: Everything is densely packed, but there is still movement.

**Question:** What is the smallest building block of life that can replicate?

> cells

**Question:** How many different cells are in a typical human?

> 200

**Question:** What are the parts of the cell called?

> organelles

**Question:** Which part of the cell is called the "powerhouse"?

> mitochondria

**Question:** What part of a plant is involved with photosynthesis?

> chloroplast

**Question:** What is mitosis?

> cell division

**Question:**  Who first used the term cell?

> Robert Hooke

**Question:** How many elements are found in amounts larger than trace amounts \(0.01%\) in our bodies?

> 11

**Question:** When communities of living things interact with non living things they are called ... ?

> ecosystem

**Question:** The most common molecule in the human body is ... ?

> Water: H\_2O

**Question:** What do bacteria have in common?

> Single Cells

**Question:** What is a gene?

> A gene is a region of DNA, which contains all information for the creation of an entire RNA strand.

**Question:** What is DNA made out of?

> DNA is a linear polymer out of 4 bases / nucleotides. DNA exists in cells mainly as a two-stranded structure called the double helix. Each of the bases has a complementary base.
>
> * G: Guanine =&gt; Cytosine
> * A: Adenine =&gt; Thymine
> * T: Thymine =&gt; Adenine
> * C: Cytosine =&gt; Guanine

**Question:** What is RNA made out of?

> RNA is a single stranded linear polymer out of 4 bases / nucleotides.
>
> * G: Guanine
> * A: Adenine
> * U: Uracil
> * C: Cytosine

**Question:** Do all organisms use the same amino acids / codons?

> Different organisms use the same amino acids for proteins. However, they differ in their codon usage \(which RNA triplets are translated into which amino acid\).

**Question:** How many proteins does a typical human have?

> Between 20.000 and 25.000 different kinds of proteins.

**Question:** What are functions of proteins?

> * Defense \(e.g. antibodies\)
> * Structure \(e.g. collagen\)
> * Enzymes \(metabolism, catabolism\)
> * Communication / Signaling \(e.g. insulin\)
> * Ligand binding / Transport \(e.g. hemoglobin\)
> * Storage \(e.g. ferritin\)

**Question:** How many residues long are typical proteins?

> Between 35 and 30.000 residues. The median is around 400.

**Question:** Do proteins consist of units?

> Proteins are built up of several domains. Most proteins have more than 2 domains.

**Question:** How many proteins are known?

> About 85 millions sequences are known. However, the 3D structure \(experimentally determined\) of only 120.000 proteins is known.

**Question:** Is this gap \(known sequences vs known 3D structure\) expected to increase?

> Yes, the gap is expected to increase. The amount of new sequences has increased drastically \(far faster than Moore's Law\) in the past. This is expected to continue. Advances in experimentally determining protein 3D structure could only improve marginally, but today experimentally determining the 3D structure of a proteins still costs about 100 000 EUR.

**Question:** How much data is produced by one sequencing machine per day?

> At full capacity about 5 - 10 terabytes of data per day.

### 3.3.3 Lecture 2: Introduction Protein Structure

**Question:** How many different amino acids are there?

> 20

**Question:** How do amino acids differ? What do they have in common?

> Different amino acids have different side-chains, which influence the chemical features of the respective amino acid. All of them share the same backbone.

**Question:** In which different feature groups can you categorize amino acids?

> polar, non-polar, acidic \(negatively charged\), basic \(positively charged\)

**Question:** Draw the basic chemical structure of an amino acid.

```
H   R   O
 \  |  //
  N-C-C
 /  |  \
H   H   O-H
```

**Question:** How are amino acids linked together to form a protein?

> In the translation process, a **Ribosome** translates a **mRNA** strand to a protein, by decoding the RNA triplets into amino acids and then linking the amino acids by peptide bonds. They chaining ALWAYS happens from the **N-Terminus** to the **C-Terminus** releasing an H20 molecule as part of the reaction.

**Question:** What is the definition of a 'domain'?

> A domain is a protein sequence, which when put into solvent adopts a unique 3D structure on its own.

**Question:** How many domains does a protein have?

> * 61% of proteins in the PDB are single domain
> * 28% of proteins in the PDB are in 62 proteomes
>
> **Problem:** This is a biased view on proteins. The 3D structure of Single-Domain-Proteins is easier to experimentally determine, so more Single-Domain-Proteins have been analyzed.

**Question:** Can domains overlap?

> Yes, it can happen. However, it is not what is typically observed** .**

**Question:** How can we compare 3D structures?

> One solution would be to align the corresponding residues of both sequences / 3D structures and take the **Root Mean Square Deviation**. \(If one pair lies very far apart, it will result in an extremely low score\)
>
> $$RMSD(A,B)= \sum_{i=0}^n ({r_i}^a - {r_i}^b )^2$$
>
> If the score is below a certain threshold, it is a match, otherwise it is not.

**Question:** How can align and compare the structure of 2 proteins?

> 1\) Find the corresponding points \(residues that match in 3D\)  
> 2\) Find Superposition independent of domain movements and calculate score \(e.g. RMSD\)

**Question:** Why is global protein comparison most of the time impossible?

> The definition of protein enforces a per residue comparison \(no scaling\). Hence only proteins of the \(almost\) the same length can be compared globally. Since proteins are between 35 and 30.000 residues long, global comparison does not make sense in most of the cases.

**Question: **What is the difference between global and local alignment?

> In **global alignment** two structures / sequences are compared from beginning to end \(compare the whole thing\).  
> In **local alignment** however, subunits \(domains\) of the proteins are aligned. \(Problem: What is a valid unit? Where to cut?\)

**Question:** How to decide what is a valid unit for local comparison of 2 proteins?

> ❓ \(I couldn't identfiy a valid answer in the lecture recording\)

**Question:** Which comparison not using cartesian RMSD could be used for comparison?

> 2D distance map: difference of differences. Only information about the chirality \(mirror image\) is lost.

### 3.3.4 Lecture 3: Alignments I

**  
Question:**Why compare 3D shapes, when we are after function? Why not compare function?

> Because ...
>
> * we cannot compare function directly
> * structure is related to function
> * we CAN compare 3D structures
> * sometimes: similar structure -&gt; similar function

**Question:** How do we get protein 3D shapes?

> * primarily by experiment \(most accurate\)
> * computational biology \(most inferences\)

**Question:** How much does it cost to experimentally determine the 3D shape of a protein?

> Today it costs on average about 100 000 $ per protein.

**Question:** What are the 3 sections found in the tree of life?

> bacteria, archaea, eukaryotes

**Question:** What does Homology stand for?

> Here \(in the context of genes\), it describes proteins originating from a common ancestor. It is also frequently used to describe 'similar structure' for genes / proteins.

**Question:** Why do linear gap penalties not model the reality of related genes / proteins well?

> With a linear gap penalty \(N gaps cost N\*x\) equally distributed gaps would be as expensive as clustered gaps. Biologically, gaps clustered to blocks, are however far more likely to occur, while the protein maintains similar structure / function. It is more realistic to use an **Affine gap penalty **with higher costs for opening a new gap.

**Question:** What is better? High sequence identity of a short \(local\) sequence, or worse sequence identity when matching a longer sequence? How can we decide?

> Compile the probability of randomly matching a sequence considering the background distribution. The result of this would be a substitution matrix such as BLOSUM62.

**Question:** Is identity the best way to match two sequences?

> Not necessarily: What we really find is similar biological function. Some amino acids might have similar biophysical features and could be swapped without any significant influence on the structure of the protein. Such matches should also be considered 'postive'.
>
> Building a scoring matrix based on evolutionary conserved residues does optimize the algorithm. \(e.g. BLOSUM62\)

**Question:** What is the biological assumption behind an insertion when comparing sequences?

> Through evolutionary changes in the DNA \(e.g. a point mutation\) a new bump \(= amino acid\(s\)\) was introduced. Implicitly it is also assumed similar structure -&gt; similar function.

**Question:** Why do linear gap penalties not model the reality of related genes / proteins well?

> With a linear gap penalty \(N gaps cost N\*x\) equally distributed gaps would be as expensive as clustered gaps. Biologically, gaps clustered to blocks, are however far more likely to occur, while the protein maintains similar structure / function. It is more realistic to use an**Affine gap penalty**with higher costs for opening a new gap.

**Question:** Does dynamic programming give the best solution?

> Yes, dynamic programming produces one optimal solution. \(There could be others, though\)

**Question:** What are issues with dynamic programming?

> * Time used: O\(n^2\)
>   * Especially a problem, when comparing one protein agains the entire database.
> * How to choose parameters?
>   * Gap penalties
>   * substitution matrix

**Question:** How can we speed up the alignment of sequences?

> 1\) Hashing \(fast and dirty\).  e.g. BLAST

**Question:** How does BLAST \(Basic Local Alignment Search Tool\) work?

> 1. Start with indexed \(hashed\) seeds \(words of size = 3\) and find matching proteins
> 2. Extend matching 'words' into both directions
> 3. Begin dynamic programming from these strong local hits

### 3.3.5 Lecture 4: Alignments I

### 3.3.6 Lecture 5: Comparative Modeling

### 3.3.7 Lecture 6: Secondary Structure Prediction 1 ❓

### 3.3.8 Lecture 7: Secondary Structure Prediction 2

**Question: **Relate the terms **Local** and **Global alignment** to the terms **Sequence-Sequence** and **Sequence-Profile**.

> Global alignments refers to aligning sequences \(proteins\) from start to end. Local alignments refers to only aligning parts of the sequences \(e.g. 50 residues\).  
> Throughout Sequence-Sequence, Sequence-Profile and Profile-Profile methods both global and local alignment can be used. I practice mostly local alignment is done.

**Question:** What would be a simple method to predict secondary structure?

> 1\) Take known structure  
> 2\) Find longest consecutive run of motifs that **ONLY** occur in one of the 3 states: H \(Helix\), E \(Strand\), O \(Other\)  
> 3\) Check unknown sequence against found motifs

**Question**: What was the first secondary structure prediction method?

> Assuming that a **Proline** would break a helix, the occurrences of proline in a sequence was used to predict helices.

**Question:** Where do we get the secondary structures from?

> From the DSSP, which defines 8 states in total based on H-bond patterns.

**Question:** What is the 1st generation of secondary structure prediction based on? What was the accuracy? Was is successful?

> * Based on single residues
> * Between 50% and 55% accuracy \(Q3\)
> * Clearly better than random - so it can be considered a success

**Question:**How did the second generation of secondary structure prediction improve? Name one algorithm.

> Instead of using only single amino acids, it would consider a sliding window of the residues around a center amino acid.**Example:**GORIII, with a Q3 accuracy of 55% - 60%

**Question:**What were problem of secondary structure prediction until 1994?

> * the maximum accuracy of predictions was expected to be 65%
> * β-sheet prediction was below 40%
> * many predicted segments where too short to appear in nature

**Question: **How can the performance of secondary structure prediction be measured?

> One way to do it, would be to calculate the **Q3** accuracy of a method against a test set. The Q3 accuracy is the **number of correctly categorized residues into one of the categories helix, strand, other divided by the total amount of residues.**

**Question:** How can the introduction of a new hidden layer in a neural network be described by means of a simple graph?

> Each new hidden layer basically introduces a new 'decision line' which can separate datapoints into different categories.

**Question:** What is cross-validation in the context of Machine Learning and why do we need it?

> Cross Validation in a method for estimating the performance of a predictive model \(e.g. a neural network\). To use it, the available dataset is split in 3 categories, 1\) a training set, 2\) a cross-training set and 3\) a test set.  
> 1\) The training set is used to train the model  
> 2\) The cross-training set is used to estimate the performance of the model after x training steps  
> 3\) The test set is used to assess the final performance of the model after training is finished  
>   
> The cross-training set is needed to decide, when to stop training \(when overtraining sets in\) and to tweak certain parameters before running against the test-set.

**Question: **Did balanced training improve the Q3 prediction accuracy? Which assumption did it prove wrong?

> Balanced training actually decreased the Q3 accuracy. However, it did improve the prediction accuracy for strands significantly, falsifying the hypothesis that strands could not be predicted with local information.

**Question:** Which problem did PHDSec solve? How did it accomplish it?

> By introducing a **Structure-to-Structure** prediction model, PHDSec improved the prediction of too short segment. The Structure-to-Structure network would take structure \(helix, strand, other\) prediction of a sequence as input and predict segments based on them.

### 3.3.9 Lecture 8: Secondary Structure Prediction 3

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

**Question:** In terms of CPU, is sequence-sequence as fast as sequence profile?

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

**Question:** When training a neural network, how do you choose the next training sample from your test set? Why so?

> Randomly, to avoid correlations

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

**Question:** Does adding global information improve ProfSec prediction?

> Yes it does. While the Q3 accuracy \(per residue\) is not improved, the Q4 accuracy \(per protein\) does improve.

### 3.3.10 Lecture 9: Membrane Structure Prediction

**Question:** What are the requirements of a cell membrane?

> * separate the content of the cell from its surroundings
> * control traffic into and out of the cell
>   * keep malicious things out
>   * let good things in
> * must be a dynamic structure

**Question:** What are the 4 main structural components of the cell membrane?

> Carbohydrates, Cholesterol, Phospholipids, Proteins

**Question:** What is the cell membrane mainly made out of?

> The cell membrane is a so called **lipid bilayer** of **phospholipids**. Phospholipids have a non-polar, hydrophobic tail \(membrane center\) and a polar, hydrophilic head \(outside of membrane\).

**Question:** What are functions of membrane proteins?

> * help to be recognized by immune cells
> * transport proteins control substance flow in and out of the cell
> * receptor proteins bind hormons, which can change cell function
> * provide structural stability

**Question:** Can membrane proteins easily move around?

> It depends:
>
> * Membrane proteins can easily move laterally
> * But it is hard to move into / out of the lipid bilayer

### 3.3.11 Lecture 10: TMSEG

### 3.3.12 Lecture 11: Beta Membrane and Accessibility

### 3.3.13 Lecture 12: Protein Disorder



