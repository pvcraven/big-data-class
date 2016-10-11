Data Sets
=========

The easiest subjects to find data on are sports, the economy, health, education,
and crime.

Meta-sets
---------

* `U.S. Government Open Data <https://www.data.gov/>`_ (Over 189,000 data sets)
* `U.S. Census Bureau <http://www.census.gov/data.html>`_
* `Kaggle Data Sets <https://www.kaggle.com/datasets>`_ Lots of different data sets and some analysis tools as well.
* `Google Public Data <https://www.google.com/publicdata/directory>`_
* `Amazon Public Datasets <https://aws.amazon.com/datasets/>`_
* `Awesome Public Datasets <https://github.com/caesar0301/awesome-public-datasets>`_

Health
------

* `HealthData.gov <http://www.healthdata.gov/search/type/dataset>`_
* `World Health Organization <http://www.who.int/gho/en/>`_
* `County Health Rankings <http://www.countyhealthrankings.org/rankings/data>`_
* `Center for Disease Control and Prevention <http://www.cdc.gov/datastatistics/>`_ (CDC)
    * `Sexually Transmitted Disease Morbidity <http://wonder.cdc.gov/std.html>`_
    * `Trend Tables <http://www.cdc.gov/nchs/hus/contents2015.htm>`_


Crime
-----

* `Law Enforcement Deaths <https://www.odmp.org/search/year>`_
* `People Killed by Police <http://www.theguardian.com/us-news/ng-interactive/2015/jun/01/the-counted-police-killings-us-database#>`_
* `Uniform Crime Reporting Statistics <http://www.ucrdatatool.gov/>`_
* `Crime in the U.S. <https://ucr.fbi.gov/crime-in-the-u.s>`_ (Click on the year, then click on the report, then find the data tables.)

Education
---------

* `NCAA Graduation Success Rates <http://www.icpsr.umich.edu/icpsrweb/NCAA/studies/30022>`_
* `National Center for Education Statistics <https://nces.ed.gov/ipeds/datacenter/>`_ (IPEDS)

Economy
-------

* `US Budget, Deficit, and Debt <https://www.whitehouse.gov/omb/budget/historicals>`_
* `US Oil Imports <https://www.eia.gov/dnav/pet/pet_move_impcus_a2_nus_ep00_im0_mbbl_m.htm>`_
* `Minnesota Public Payroll Data <https://mn.gov/mmb/transparency-mn/payrolldata.jsp>`_

Entertainment
-------------

* `Pokemon Stats <https://www.kaggle.com/abcsds/pokemon>`_

Sports
------

* `College Football Statistics <http://www.cfbstats.com/>`_
* `NCAA Statistics <http://web1.ncaa.org/stats/StatsSrv/careersearch>`_

Weather
-------

Weather from NOAA (`Site <https://www.ncdc.noaa.gov/cdo-web/datasets>`_, `FTP <ftp://ftp.ncdc.noaa.gov/pub/data/ghcn/daily/>`_)

File info:

* weather/ghcnd-stations.txt -- List of stations. Egrep what you want
* weather/*.dly -- Weather files. Format description is `here <ftp://ftp.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt>`_

Example processing weather data:

* ``egrep TMAX USC00134063.dly | sed 's/^.\{11\}//' | sed 's/[0−9] .*/\1/' | sed 's/TMAX//' | sed 's/^[* 0−9]{4}/\1 /' | sed 's/^.{11}[0−9]/\1\.\2/' > ../craven.csv``
* ``egrep TMAX USC00134063.dly`` # Search the text file for 'TMAX* ' which is the temperature maximum
* ``sed 's/^.\{11\}//'`` # Use sed and regular expressions. From * the beginning of the line, remove 11 characters
* ``sed 's/[0−* 9] .*/\1/'`` # Use sed to remove all of the line after the last temp reading.
* ``sed 's/TMA* X//'`` # Remove the TMAX from the line
* ``sed 's/^[0−9]{4}/\1 /'`` # Add a space after the year so it doesn't run into the month
* ``sed 's/^.{11}[0−9]/\1\.\2/'`` # Add a decimal into the number, because 345 is actually 34.5
* ``> ../craven.csv`` # Redirect to a file. Do it one directory up because there are way too many files here