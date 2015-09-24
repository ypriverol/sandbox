sga
=====
de novo sequence assembler using string graphs http://genome.cshlp.org/content/22/3/549


available software
--------
`
sga 0.10.13
bamtools 2.4.0
sparsehash 2.0.2
jemalloc 4.0.2
pysam==0.8.3
ruffus==2.6.3
`


how to build
------------
`docker build --rm -t biodckrdev/sga 0.10.13/.`


how to download and install
---------------------------
`docker pull biodckrdev/sga`


how to use
------------
`docker run --rm biodckrdev/sga <options> <files>`


software website
----------------
`https://github.com/jts/sga`


support
-------
we do not provide support for the containerized software, only to aspects regarding the container itself
and its usage. For more information about the software usage, please refer to the publication.


licence
-------
the license present in this repository refers only to the instructions necessary to create the containers, we do not provide or apply this repository license over the containerized software. Each software is distributed with a specific license selected by the developer group. For more information on that, please check the respective publication.


about
-----
If you are looking for containerized bioinformatics software;

visit the [Bio Docker](http://biodocker.github.io "Bio Docker") website.

visit the [GitHub page](https://github.com/BioDocker/) for the source code.

visit the [Docker Hub](https://registry.hub.docker.com/repos/biodckr/) for the available images.


maintainers
-----------
* Felipe da Veiga leprevost <felipe@leprevost.com.br>
* Yasset Perez-Riverol <ypriverol@gmail.com>
* Saulo Alves Aflitos <sauloal@gmail.com>
