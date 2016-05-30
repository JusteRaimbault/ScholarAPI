# Scholar API

[![DOI](https://zenodo.org/badge/18922/JusteRaimbault/ScholarAPI.svg)](https://zenodo.org/badge/latestdoi/18922/JusteRaimbault/ScholarAPI)


An API to retrieve information from scholar.


## Description

Basic information retrieval from scholar (titles, id, publication year).

## Usage

### General

Need to be used conjointly with a running TorPool (https://github.com/JusteRaimbault/TorPool) ; Run the pool in background : `java -jar lib/torpool.jar Nthreads` with a reasonable number of threads (30 is generally ok). Most of tor nodes are blocked, resulting in a slow general performance, consider running your scripts also in background and adapt data storage accordingly.

### Javadoc

Javadoc for the API : *forthcoming*

### Scripts

Compiled script in jars for specific tasks :
  * Citation Network construction : given an initial corpus, retrieves incoming citations to a given level. Usage (when torpool running in same dir): `java -jar citationNetwork.jar $CORPUS $RESFILEPREFIX $LEVEL` . `$CORPUS` is csv file name for initial corpus, with at least two columns, in order : reference titles, reference scholar ID (not necessary, put empty column if not available, but ensures that the reference will be found, in case of title variations - matching with scholar records is done on Levenstein distance on title (< 4) [and same year when using the API with year record]) ; `$RESFILEPREFIX` is the name of output files, that will be respectively : `$RESFILEPREFIX.csv` final corpus (title,id,year), `$RESFILEPREFIX_links.csv` links (from,to), `$RESFILEPREFIX_progress.csv` progress file (useful for large corpus, already retrieved references will not be taken into account when relaunching an interrupted process e.g.) ; `$LEVEL` gives depth level of citation network : starting at 1, will retrieve citing references of initial corpus and deeper levels if > 1.
