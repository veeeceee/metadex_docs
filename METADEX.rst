An Example Workflow with a Sample Data Set (Lagoons)
====================================================

First, if you haven't installed the package, you can do so using PyPI
(in the terminal):

.. code:: python

    !pip install metadex

Let's get started:

.. code:: python

    import metadex
    %matplotlib inline

Reading Annotations from Study into Metadex
-------------------------------------------

In the previous Section, we downloaded a series of annotations from a
lagoons data set on MG-RAST. Now, we will load those annotations into
metadex to get started, 'lagoon study' being the folder/directory the
annotations were downloaded into:

.. code:: python

    lagoons = metadex.Study('lagoon study')
    lagoons.read_annotations()

Output
~~~~~~

When this step is complete the lagoon study directory should look as
follows:

lagoon study - nador\_1.tsv - nador\_2.tsv - oualidia\_1.tsv -
oualidia\_2.tsv - nador\_1\_counts.csv - nador\_2\_counts.csv -
oualidia\_1\_counts.csv - oualidia\_2\_counts.csv

Load Gene Counts Matrix into Study
----------------------------------

In the previous section, you downloaded the gene counts matrix from
MG-RAST's 'Analyze' interface. Load the separated text file using its
location, because it will help with finding genes of interest:

.. code:: python

    lagoons.load_gene_matrix(filename)

Input
~~~~~

folder should be the name of the directory containing individual counts
files, each with the formatting of \*[group]\_[ID]\*.csv where *
represents wildcard.

Can accept any folder name, so can load counts data that has been
annotated and/or normalised.

Output
------

Creates a Study, which contains:

Study.counts => list of counts DataFrames Study.groups => list of
corresponding groups Study.iDs => list of corresponding ID within the
groups

Determining Genes of Interest
-----------------------------

While MG-RAST allows you to visualise genes that have changed using
their 'Analyze' interface, metadex leverages the Boruta feature
selection method to determine differences between groups and samples and
each level of functional hierarchy. Boruta uses a specific threshold for
feature selection (see link here: []) and each can be manipulated as per
yourneeds.

.. code:: python

    lagoons.determine_genes_of_interest( lvl1pct=70, lvl2pct=70, lvl3pct=60, fxnpct=40)

At each functional level, Boruta will provide selected and weakly
selected features. These should help guide the user as to potential
genes of interest worth focusing on

Normalising Counts
------------------

Counts need to be normalised. Metadex takes care of this too:

.. code:: python

    lagoons.normalise_counts()

Input
~~~~~

Study.counts

Output
~~~~~~

normalises Study.counts via rarefaction and recodification Study.counts
will be replaced with the rarefied and recodified version

When this step is complete the lagoon study directory should look as
follows:

lagoon study - nador\_1.tsv - nador\_2.tsv - oualidia\_1.tsv -
oualidia\_2.tsv - nador\_1\_counts.csv - nador\_2\_counts.csv -
oualidia\_1\_counts.csv - oualidia\_2\_counts.csv normalised\_counts -
nador\_1\_counts\_norm.csv - nador\_2\_counts\_norm.csv -
oualidia\_1\_counts\_norm.csv - oualidia\_2\_counts\_norm.csv

Annotating with Lineage Information
-----------------------------------

The counts data has species info, but this may obscure trends that occur
along higher taxonomic levels. Thus, metadex updates the counts data
with correspondin information for phylum, class, order, and family:

.. code:: python

    lagoons.add_lineage_info()

This step requires persistent communication with the Entrez servers, and
will take a while. Thankfully it outputs each query to the console.

lagoons.counts will have additional columns denoting phylum, class,
order, and family for each annotation When this step is complete the
lagoon study directory should look as follows:

lagoon study - nador\_1.tsv - nador\_2.tsv - oualidia\_1.tsv -
oualidia\_2.tsv - nador\_1\_counts.csv - nador\_2\_counts.csv -
oualidia\_1\_counts.csv - oualidia\_2\_counts.csv normalised\_counts -
nador\_1\_counts\_norm.csv - nador\_2\_counts\_norm.csv -
oualidia\_1\_counts\_norm.csv - oualidia\_2\_counts\_norm.csv
norm\_taxonomy - nador\_1\_counts\_norm\_taxonomy.csv -
nador\_2\_counts\_norm\_taxonomy.csv -
oualidia\_1\_counts\_norm\_taxonomy.csv -
oualidia\_2\_counts\_norm\_taxonomy.csv

Sidebar: Loading Study Counts into Metadex
------------------------------------------

If you have counts files, you can load them into a Metadex study:

.. code:: python

    lagoons = metadex.Study('lagoon study')
    #If your previous step was read_annotations:
    #lagoons.load_counts('lagoon study')
    #If your previous step was normalise_counts:
    #lagoons.load_counts('normalised_counts')
    #If your previous step was add_lineage_info:
    lagoons.load_counts('norm_taxonomy') 

Can accept any folder name, so can load counts data that has been
annotated and/or normalised.

Creates a Study, which contains: lagoons.counts => list of individual
counts DataFrames, one per sample lagoons.groups => list of
corresponding groups for each sample lagoons.iDs => list of
corresponding ID within the groups

Focusing on Gene (User Query)
-----------------------------

Once the user has a potential gene or gene family of interest in mind,
they can zoom in to that subset of the data.

.. code:: python

    lagoons.focus_on_gene('aspartokinase') 

Visualising Diversity for Gene
------------------------------

Understanding how a gene seen in an environment is distributed is a key
insight to understanding the link between gene function and environment.
Metadex provides ways to depict both the quantitative and qualitative
facts of this relationship within one' study:

.. code:: python

    lagoons.visualise_diversity_for_gene('Aspartokinase', 'aspartokinase')

.. code:: python

    import brunel
    import pandas as pd
    aspartokinase = pd.read_csv('lagoon study_Aspartokinase_avg.csv')
    %brunel data('aspartokinase') treemap x(order) y(family) color(order) size(nador) sort(nador) label(organism, nador) tooltip(#all) :: width=2000, height=2000

.. code:: python

    aspartokinase = pd.read_csv('lagoon study_Aspartokinase_avg.csv')
    %brunel data('aspartokinase') treemap x(order) y(family) color(order) size(oualidia) sort(oualidia) label(organism, oualidia) tooltip(#all) :: width=2000, height=2000

Try this out for some of the other genes (consult the
determine\_genes\_of\_interest output if you aren't sure which genes to
look at)
