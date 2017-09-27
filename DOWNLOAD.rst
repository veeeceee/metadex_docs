Download the Sample Data Set
============================

First, if you haven't installed the package, you can do so using PyPI
(in the terminal):

.. code:: python

    #!pip install metadex
    import metadex

Get Study Information from MG-RAST
----------------------------------

MG-RAST assigns each metagenome a metagenome ID (mgm...). For each
metagenome you would like to include in your study, you will need: -
metagenome ID - corresponding assigned group - corresponding assigned
sample ID (within the group can be 1, 2, 3; or something more specfic)

Download Gene Counts Matrix from MG-RAST
----------------------------------------

1. Go to **Analyze** section of MG-RAST

2. Select the following metagenomes: - mgm739968.3 - mgm739969.3 -
   mgm739970.3 - mgm739971.3

3. Select matrix

4. Export to CSV (tab-separated CSV)

Getting Annotations from MG-RAST
--------------------------------

Based on the information above, we can download the full counts (the
main information) directly via API:

.. code:: python

    metadex.get_all_async('lagoon study', {'mgm4739968.3':'nador_lagoon', 'mgm4739969.3':'oualidia_lagoon', 'mgm4739970.3': 'oualidia_lagoon', 'mgm4739971.3':'nador_lagoon'}, 'RefSeq', evalue=5, identity=60, length=15) 


First MetaDEx creates a directory named 'lagoon study' in which it
downloads the annotations for each metagenome (e.g. mgm4739968.3) to
corresponding tab- separated files named for the group and ID (e.g.
nador\_lagoon\_1\_counts.tsv).

When this step is complete the lagoon study directory should look as
follows:

lagoon study - nador\_1.tsv - nador\_2.tsv - oualidia\_1.tsv -
oualidia\_2.tsv
