Large Text Data Sets
====================

Names
-----

Names for the whole U.S. are in the ``names`` folder. Names broken down on a
state-by-state basis are in the ``names_by_state`` folder.

Original source is the
`Social Security Administration <https://www.ssa.gov/oact/babynames/limits.html>`_.

FEC
---

`FEC Data <http://www.fec.gov/finance/disclosure/ftp_download.shtml>`_

Contributions to political campaigns
political/individual_contributions.txt (`fields definitions <http://www.fec.gov/finance/disclosure/metadata/DataDictionaryContributionsbyIndividuals.shtml>`_)

Automotive
----------

Complaints, defect investigations, and recalls for different
cars. Source is the `National Highway Traffic Safety Administration <http://www-odi.nhtsa.dot.gov/downloads/>`_.


`A list of fields and descriptions for the 'complaints' table <http://www-odi.nhtsa.dot.gov/downloads/folders/Complaints/CMPL.txt>`_.

Medicare
--------

Medicare claims from `Centers for Medicare & Medicaid Services <https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Provider-Charge-Data/Physician-and-Other-Supplier2014.html>`_

Weather
-------

All of this data is in the ``weather`` folder.

The original source for the weather data is from
NOAA (`Site <https://www.ncdc.noaa.gov/cdo-web/datasets>`_, `FTP <ftp://ftp.ncdc.noaa.gov/pub/data/ghcn/daily/>`_)

File info:

* weather/ghcnd-stations.txt -- List of stations. Egrep what station you want.
* weather/\*.dly -- Weather files. Format description is `here <ftp://ftp.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt>`_

Example processing weather data:

* ``egrep TMAX USC00134063.dly | sed 's/^.\{11\}//' | sed 's/[0−9] .*/\1/' | sed 's/TMAX//' | sed 's/^[* 0−9]{4}/\1 /' | sed 's/^.{11}[0−9]/\1\.\2/' > ../craven.csv``
* ``egrep TMAX USC00134063.dly`` # Search the text file for 'TMAX* ' which is the temperature maximum
* ``sed 's/^.\{11\}//'`` # Use sed and regular expressions. From * the beginning of the line, remove 11 characters
* ``sed 's/[0−* 9] .*/\1/'`` # Use sed to remove all of the line after the last temp reading.
* ``sed 's/TMA* X//'`` # Remove the TMAX from the line
* ``sed 's/^[0−9]{4}/\1 /'`` # Add a space after the year so it doesn't run into the month
* ``sed 's/^.{11}[0−9]/\1\.\2/'`` # Add a decimal into the number, because 345 is actually 34.5
* ``> ../craven.csv`` # Redirect to a file. Do it one directory up because there are way too many files here
