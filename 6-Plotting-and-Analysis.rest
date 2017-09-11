Pre-requisites
--------------------
* You have created a project and know the ACTION-ID (use expipe-browser to find it).
* If it is your first anaconda/expipe session of the day, Open Anaconda ``activate expipe`` - eller må man også ``activate env my project_id`` ?????

Plotting and analysis
--------------------

**Plotting with notebook**::

  $ expipe generate-notebook ACTION-ID --run

``kernel -> restart and run all``

**Make png figurer**::

  $ expipe analyse ACTION-ID --analyse spatial --analyse spike-stat

If you only want to look at a particular channel group::

  $ expipe analyse ACTION-ID -a all --channel-group 0

**Register cells and transfer data to norstore**

When your are finished with the analysis you want to write a summary of your findings, you can
annotate the action with::

  $ expipe annotate ACTION-ID --tag GC --tag BC --message "found a beautiful grid cell on channel group 2"

*Example tags:*
Bare dritt: no, Good shit: yes, Vet ikke: maybe, Head direction: HD, Grid cell: GC,
Place cell: PC, Spatial cell: SC, Boarder cell: BC.

The tags you want to use should be added to POSSIBLE_TAGS

Go to `SERVER/PROJECT/ACTION-ID/main.exdir/analysis` to check out the results.
