SnpEff
=====
Genetic variant annotation and effect prediction toolbox. 


available software
--------
`SnpEff 4.1 K (2015-09-07)`


how to build
------------
`docker build --rm -t biodckrdev/snpeff 4.1k/.`


how to download and install
---------------------------
`docker pull biodckrdev/snpeff`


how to use
------------
`docker run --rm -it biodckrdev/snpeff <options> <files>`
`docker run --rm -it biodckrdev/snpeff snpeff databases`
`docker run --rm -it biodckrdev/snpeff snpsift`


software website
----------------
```
http://sourceforge.net/projects/snpeff/
http://snpeff.sourceforge.net/
```


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
