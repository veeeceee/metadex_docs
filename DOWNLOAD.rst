An Example Workflow with a Sample Data Set
==========================================

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

.. code:: json

    [
     {
      "ename": "NameError",
      "evalue": "name 'errno' is not defined",
      "output_type": "error",
      "traceback": [
       "\u001b[0;31m---------------------------------------------------------------------------\u001b[0m",
       "\u001b[0;31mFileExistsError\u001b[0m                           Traceback (most recent call last)",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/metadex/download_files.py\u001b[0m in \u001b[0;36mcreate_path\u001b[0;34m(path)\u001b[0m\n\u001b[1;32m     22\u001b[0m     \u001b[0;32mtry\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m---> 23\u001b[0;31m         \u001b[0mos\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mmakedirs\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mpath\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m     24\u001b[0m     \u001b[0;32mexcept\u001b[0m \u001b[0mOSError\u001b[0m \u001b[0;32mas\u001b[0m \u001b[0mexception\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/os.py\u001b[0m in \u001b[0;36mmakedirs\u001b[0;34m(name, mode, exist_ok)\u001b[0m\n\u001b[1;32m    240\u001b[0m     \u001b[0;32mtry\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 241\u001b[0;31m         \u001b[0mmkdir\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mname\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mmode\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    242\u001b[0m     \u001b[0;32mexcept\u001b[0m \u001b[0mOSError\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;31mFileExistsError\u001b[0m: [Errno 17] File exists: 'lagoon study'",
       "\nDuring handling of the above exception, another exception occurred:\n",
       "\u001b[0;31mNameError\u001b[0m                                 Traceback (most recent call last)",
       "\u001b[0;32m<ipython-input-2-bb0b0a103923>\u001b[0m in \u001b[0;36m<module>\u001b[0;34m()\u001b[0m\n\u001b[0;32m----> 1\u001b[0;31m \u001b[0mmetadex\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mget_all_async\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m'lagoon study'\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m{\u001b[0m\u001b[0;34m'mgm4739968.3'\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m'nador_lagoon'\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m'mgm4739969.3'\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m'oualidia_lagoon'\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m'mgm4739970.3'\u001b[0m\u001b[0;34m:\u001b[0m \u001b[0;34m'oualidia_lagoon'\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m'mgm4739971.3'\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m'nador_lagoon'\u001b[0m\u001b[0;34m}\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0;34m'RefSeq'\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mevalue\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0;36m5\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0midentity\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0;36m60\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mlength\u001b[0m\u001b[0;34m=\u001b[0m\u001b[0;36m15\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/metadex/download_files.py\u001b[0m in \u001b[0;36mget_all_async\u001b[0;34m(study, metagenomeGroupDict, source, evalue, identity, length)\u001b[0m\n\u001b[1;32m    117\u001b[0m     \u001b[0mloop\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0masyncio\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mget_event_loop\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m)\u001b[0m \u001b[0;31m# event loop\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    118\u001b[0m     \u001b[0mfuture\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0masyncio\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mensure_future\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mdownload_all\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0murls\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mgeneOnlyUrl\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mstudy\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mmetagenomeGroupDF\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0msource\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mevalue\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0midentity\u001b[0m\u001b[0;34m,\u001b[0m \u001b[0mlength\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m)\u001b[0m \u001b[0;31m# tasks to do\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 119\u001b[0;31m     \u001b[0mloop\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mrun_until_complete\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mfuture\u001b[0m\u001b[0;34m)\u001b[0m \u001b[0;31m# loop until done\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    120\u001b[0m     \u001b[0mos\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mchdir\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m'..'\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    121\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/asyncio/base_events.py\u001b[0m in \u001b[0;36mrun_until_complete\u001b[0;34m(self, future)\u001b[0m\n\u001b[1;32m    385\u001b[0m             \u001b[0;32mraise\u001b[0m \u001b[0mRuntimeError\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m'Event loop stopped before Future completed.'\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    386\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 387\u001b[0;31m         \u001b[0;32mreturn\u001b[0m \u001b[0mfuture\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mresult\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    388\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    389\u001b[0m     \u001b[0;32mdef\u001b[0m \u001b[0mstop\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mself\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/asyncio/futures.py\u001b[0m in \u001b[0;36mresult\u001b[0;34m(self)\u001b[0m\n\u001b[1;32m    272\u001b[0m             \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_tb_logger\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0;32mNone\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    273\u001b[0m         \u001b[0;32mif\u001b[0m \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_exception\u001b[0m \u001b[0;32mis\u001b[0m \u001b[0;32mnot\u001b[0m \u001b[0;32mNone\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 274\u001b[0;31m             \u001b[0;32mraise\u001b[0m \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_exception\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    275\u001b[0m         \u001b[0;32mreturn\u001b[0m \u001b[0mself\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0m_result\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    276\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/asyncio/tasks.py\u001b[0m in \u001b[0;36m_step\u001b[0;34m(***failed resolving arguments***)\u001b[0m\n\u001b[1;32m    237\u001b[0m                 \u001b[0;31m# We use the `send` method directly, because coroutines\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    238\u001b[0m                 \u001b[0;31m# don't have `__iter__` and `__next__` methods.\u001b[0m\u001b[0;34m\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m--> 239\u001b[0;31m                 \u001b[0mresult\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mcoro\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0msend\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;32mNone\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m    240\u001b[0m             \u001b[0;32melse\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m    241\u001b[0m                 \u001b[0mresult\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mcoro\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mthrow\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mexc\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/metadex/download_files.py\u001b[0m in \u001b[0;36mdownload_all\u001b[0;34m(urls, geneOnlyUrl, study, metagenomeGroupDF, source, evalue, identity, length)\u001b[0m\n\u001b[1;32m     86\u001b[0m     \u001b[0mgroupList\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mmetagenomeGroupDF\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'group'\u001b[0m\u001b[0;34m]\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     87\u001b[0m     \u001b[0msampleList\u001b[0m \u001b[0;34m=\u001b[0m \u001b[0mmetagenomeGroupDF\u001b[0m\u001b[0;34m[\u001b[0m\u001b[0;34m'sample'\u001b[0m\u001b[0;34m]\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m---> 88\u001b[0;31m     \u001b[0mcreate_path\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mstr\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mstudy\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m     89\u001b[0m     \u001b[0mos\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mchdir\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mstr\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mstudy\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     90\u001b[0m     \u001b[0masync\u001b[0m \u001b[0;32mwith\u001b[0m \u001b[0maiohttp\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mClientSession\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0;34m)\u001b[0m \u001b[0;32mas\u001b[0m \u001b[0msession\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;32m/Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages/metadex/download_files.py\u001b[0m in \u001b[0;36mcreate_path\u001b[0;34m(path)\u001b[0m\n\u001b[1;32m     23\u001b[0m         \u001b[0mos\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mmakedirs\u001b[0m\u001b[0;34m(\u001b[0m\u001b[0mpath\u001b[0m\u001b[0;34m)\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     24\u001b[0m     \u001b[0;32mexcept\u001b[0m \u001b[0mOSError\u001b[0m \u001b[0;32mas\u001b[0m \u001b[0mexception\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0;32m---> 25\u001b[0;31m         \u001b[0;32mif\u001b[0m \u001b[0mexception\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0merrno\u001b[0m \u001b[0;34m!=\u001b[0m \u001b[0merrno\u001b[0m\u001b[0;34m.\u001b[0m\u001b[0mEEXIST\u001b[0m\u001b[0;34m:\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[0m\u001b[1;32m     26\u001b[0m             \u001b[0;32mraise\u001b[0m\u001b[0;34m\u001b[0m\u001b[0m\n\u001b[1;32m     27\u001b[0m \u001b[0;34m\u001b[0m\u001b[0m\n",
       "\u001b[0;31mNameError\u001b[0m: name 'errno' is not defined"
      ]
     }
    ]

First MetaDEx creates a directory named 'lagoon study' in which it
downloads the annotations for each metagenome (e.g. mgm4739968.3) to
corresponding tab- separated files named for the group and ID (e.g.
nador\_lagoon\_1\_counts.tsv).

When this step is complete the lagoon study directory should look as
follows:

lagoon study - nador\_1.tsv - nador\_2.tsv - oualidia\_1.tsv -
oualidia\_2.tsv
