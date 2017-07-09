## 3.2 Exercise Questions

> This section contains possible exam questions asked and answered as part of the exercises.

#### Exercise 2: Protein Structure

**Question:** What are the building blocks of proteins?

> * Proteins are polypeptides, which consist of amino acids as building blocks

**Question:** Define protein backbone and amino acid side chain in 1 or 2 sentences for each term.

> * **Backbone:** All amino acids have the same with an N-Terminus on one and a C-Terminus on the other side by which they are chained up into a protein. \(Always read / write from N- to C-Terminus\) 
> * **Side Chain:** Each Amino Acid has a different side chain, which equips it with unique features \(length, polar, non-polar, electrically charged\)

**Question:** How many amino acids appear in proteins? How can they be classified?

> All proteins are built from **20 different amino acids**. The can be classified into the following 5 groups /categories
>
> * positively electrically charged side chain 
> * negatively electrically charged side chain
> * polar uncharged side chains
> * hydrophobic side chains
> * special cases

**Question:** Name atom types involved in a hydrogen bond. Do S-H groups form hydrogen bonds? Why \(not\)?

> Hydrogen bonds normally involve
>
> * an **H **atom \(obviously\) as donor
> * either an **O** or **N** atom as acceptor
>
> Due to its lower electronegativity Sulfur does not engage in classical Hydrogen-Bonds. \(However nonclassical hydrogen bonds with Sulfur seem to exist, according to literature\)

**Question:** How are alpha helices held together?

> Alpha-Helices are stabilized by **hydrogen bonds** along the backbone. Every turn takes about **3,6 **residues.

**Question:** What is similar and what is different in the hydrogen bonding of the alpha helix and the beta sheet?

> * Hydrogen bonds in **Alpha Helices** are 'ultra-local' and occur along the backbone of the helix \(each 3.6 residues\)
> * Hydrogen bonds between **Beta Sheets** happen between the beta-strands \(running parallel or antiparallel\) which can be rather far apart in sequence.

**Question:** Why do we find "forbidden" areas in a Ramachandran plot?

> The Ramachandran plot shows the angles $$(\phi,\ \psi)$$ of amino acids in which alpha-helices and beta sheet are typically observed. Forbidden areas are those that are not possible due to physical constraints due to e.g. the side chain of the amino acid.

**Question:** What is a protein domain?

> A domain is a conserved (sub-)sequences of a protein, which adopts a unqiue 3D structure when put into solvent.

**Question:** How many amino acids are typically found a in a domain? Why is there a minimum/maximum size?

> Proteins domains are found between 36 and 690 residues long. Most protein domains have a length of around 100 residues.
> 
> Minimum Size: ?
> Maximum Size: ?

##### 2.2 PDB

**Question:** How many structures are stored in the PDB? How many of those are protein structures?

> About 130 000 entries can be found in the PDB, of which around 120 000 are protein structures.

**Question:** Which experimental methods are \(mainly\) used to determine the structures? How long does it on average take to find the 3D structure for one protein for each method?

> The largest part (90%) of proteins structures are determined by X-Ray crystallography, followed by NMR (9%) and Cryo-EM (1%).
> However, the number of new Cryo-EM structures is projected to overtake the number of new NMR entries in 2017. Current sciene pushing the limits of Cryo-EM resolution, makes it a promising technology for future 3D structure determination.
>
> **Costs / Time per Method**
> * X-Ray: (100 000, ?)
> * NMR: (?, ?)
> * Cryo-Em: (?, ?)

**Question:** How many human \("Homo sapiens"\) protein structures are in the PDB?

> About 37 000 protein structures of homo sapiens. (Not, sequence unique entries though)

**Question:** Why does the number of protein structures already decreases when reducing at 100% sequence identity? Why does it decrease when reducing at even lower sequence identity further?

> * The PDB has redundant 3D structures for certain proteins from different experiments. This has different reasons such as competing groups, different research goals, better resolution.
> * Since most proteins developed under evolutionary pressure, large parts of proteins of the same family share a high sequence overlap.

#### Exercise 3: Alignments

**Question:** How can you define similarity between two protein sequences?

> Two ways to define similarity are to compute the percentage of residues that were aligned
>
> * and matched on the same amino acid \(PSI, Percent Sequence Identity\)
> * and matched with a positive score in the Substitution Matrix

**Question: **What does "conservation" mean in the context of sequence alignments?

> * Conserved sequences are similar or identical \(sub\)sequences that occur within protein sequences.
> * By compiling homolgues proteins \(a family\) into a profile, it become clear, which subsequences are more conserved and thus more important for the function of the protein family

**Question:** Why are sequence alignments useful?

> * They are useful because the allow use to find the 'best' possible match between two sequences. Only this allows use to
>   * compare their 3D structure
>   * create predictions about their similarity in 3D structure
>   * make assumptions about their evolutionary relatedness

**Question:** What are the main differences in the algorithms of Global and Local alignment? Why does it make sense to not always perform a global alignment.

> * Global alignment methods always align 2 sequences from beginning to end.
> * Local alignment methods only align subsequences.
>
> * For Global alignment to be meaningful, the sequences should have similar length. Since proteins are between 35 and 30000 residues long, it does not make sense to always use global alignment.
>
> * Also when e.g. looking for proteins with a certain domain it does not make sense to use global alignment, since we are explicitly looking for subsequences.

**Question:** Which amino acids can \(with high likelihood\) be substituted for Leucin without having an effect on protein function?

> Methionine \(2\). Isoleucin \(2\), Valine \(2\), Phenylalanine \(0\), because the have a positive score in the BLOSUM62 matrix

**Question:** Which substitution is more probable according to PAM250 and according to BLOSUM62: \[a\] W &lt;&gt; F \[b\] H &lt;&gt; R

> * W \(Tryptophan\) &lt;--&gt; F \(Phenylalanine\)
>   * BLOSUM: 1
>   * PAM250: 0
> * H \(Histidine\) &lt;--&gt; R \(Arginine\)
>   * BLOSUM: 0
>   * PAM250: 2
>
> =&gt; For BLOSUM W &lt;--&gt; F is more likely to be observed  
> =&gt; For PAM250 H &lt;--&gt; R is more likely to be observed

**Question:** What is a multiple sequence alignment?

> A method to align multiple sequences against each others.
>
> * building a consensus sequence and aligning new sequences against it
> * building a search tree
> * building a profile \(like PSI-BLAST\)

**Question:** What kind of sequences are likely to be used for an MSA? In which relationship are they to each other?

> * Most likely, sequences which we assume a evolutionary relationship \(homology\) will be used. Following the homology assumption, we expect sequences with a high PSI to have a similar structure because they have a common ancestor.
> * Building up a profile with them, would then allow us to discover conserved regions and use the profile to find more candidates in the Twilight Zone with Profile-Sequence comparison.

**Question:** Why would you want to align multiple sequences? What kind of information is contained in MSAs but not directly in e.g. all-against-all pairwise alignments?

> Building up a profile with similar sequences, would  allow us to discover conserved regions which developed under evolutionary pressure.  
> By compiling such a family of proteins \(we assume that they have a common ancestor -&gt; homology\) into a profile, we can find more candidates in the Twilight Zone with Profile-Sequence comparison.

**Question:** Given your knowledge of the algorithms for pairwise alignments, how could you calculate an MSA? Is that a feasible approach? Why?

> One approach would be to sequentially align sequences against a consensus sequence. This approach, however, comes with problems such as the need for a strategy how to find the consensus for a certain amino acid at a certain position, the fact that the order of alignment might matter, etc.
>
> A better approach is the creation of a PSSM \(position specific scoring matrix\), which contains for each position of the profile the likelihood that a certain amino acid occurs there.

**Question:** You have a sequence which you would like to find in a database. Which search method and which E-value cutoff do you use, \[a\] if you know your sequence is in the database and only want to find that entry \[b\] if you would like to find homologs.

> \[a\] Pairwise alignment \(❓ ??? is this right???\)  
> \[b\] BLAST

**Question:** What is the difference between BLAST and PSI-BLAST?

> BLAST uses the BLOSUM matrix to retrieve homologs. It runs only once and returns the found sequences.
>
> PSI-BLAST uses BLAST in the first run to find homologs and build a profile. By using, and iteratively rebuilding, the profile it can find more distant \(in terms of sequence identity\) homologs with Profile-Sequence alignment.

#### Exercise 3: Resources for Bioinformatics

**Question:** How many structures in PDB have a resolution with =&lt; 2 Angstrom

> ?

**Question:** Which term from computer science you would use to describe PROSITE patterns \(e.g. PDOC00022\).

> ???
>
> -&gt; I would argue it reminds me of regular expressions, but this should be verified.  
> eg see here: [http://www.hpa-bioinfotools.org.uk/ps\_scan/PS\_SCAN\_PATTERN\_SYNTAX.html](http://www.hpa-bioinfotools.org.uk/ps_scan/PS_SCAN_PATTERN_SYNTAX.html)

**Question:** Which type of information does STRING provide?

> STRING is a secondary database which provides information about known and predicted protein interactions.

**Question:** What does PFAM-A contain?

> PFAM-A contains manually curated information about proteins families. It is especially useful, because it contains
>
> * Profile HMMs
> * Seed alignments
> * Full alignments with all hits







