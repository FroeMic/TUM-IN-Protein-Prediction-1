## 2.5 Resources for Bioinformatics

###### 08.06.2017 \| [Slides](https://www.rostlab.org/sites/default/files/fileadmin/teaching/SoSe17/PP1CS/20170608_PP1_resources.pdf) \| [Wiki](https://i12r-studfilesrv.informatik.tu-muenchen.de/sose17/pp4cs1/index.php/Resources_for_Biological_Informations_/_Formats)

---

#### 1. Keywords

##### Resources / Databases

* Represent a shared fund of knowledge
* "_data collections_" often more precise than database
* have evolved over decades \(legacy issues\)
* **primary** and **secondary** databases
* **Primary Databases**
  * Genbank / EBI / DDBJ \(nucleic acid sequences\)
  * UniprotKB \(protein sequences\)
  * PDB \(3D structures\)
* **Secondary Databases** \(contains refined of topic selected / processed informa+on derived from primary databases\)
  * STRING
  * PROSITE
  * PFAM

##### Genbank, EMBL,EBI

_The entries in the Genbank is growing exponantially!_

**Genbank:** sequence database maintained by the NCBI \(National Center for Biotechnology Information, USA\)  
**EMBL:** The European Molecular Biology Laboratory maintained by EBI \(European Bioninformatics Institute\)

**Flat File Format:** Entries come compressed as **text files** with an uncompressed size of over **700 GB**

* Records consist of 2 parts
  * Columns \(1-10\), Entry Field name
  * Remaining line with the content \(sequence\)
* Version / Accession Format
  * Unique identifier: Value of the VERSION field
  * VERSION: Accession number + "." + integer
  * Update of version ONLY when sequence changes
  * Other field values could be changed without notice

##### Uniprot

_Universal Protein Database_

* combines information from Swissprot, TrEMBL, PIR

##### Swissprot/Trembl

_Manually annotated and revied section of UniProt._

* **Annotation Process**
* 1. Sequence Curation
  2. Sequence Analysis
  3. Literature curation
  4. Family based curation
  5. Evidence attribution \(every annotation is attributed to its original source\)
  6. Quality assurance, integration and update

##### ExPasy

_Expert Protein Analysis System_

* **Categories**
  * Proteomics
  * Genomics
  * Structural Bioinformatics
  * System Biology
  * Phylogeny / Evolution
  * Populations genetics
  * Transcriptomics
  * Biophysics
  * Imaging
  * Drug Design

##### PDB

##### PDB file format

##### 

##### mmCIF

##### Accessing these databases: BioPython

##### 

##### PFAM

**Protein Families Database**: \(Especially useful **PFAM-A** with Profile HMMs, seed alignments, full alignments\)  
\(_Secondary Database\)_

##### STRING

**Proteins Interaction Network:** Known and predicted protein interactions  
\(_Secondary Database\)_

##### PROSITE

Documentation entries describing proteins domains, families, functional sites, associated patterns and profiles  
\(_Secondary Database\)_

* Domain specific descriptions
* provide reference sequence and alignments
* provide consensus pattern

#### 2. Exercises

##### 2.1 Questions

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



