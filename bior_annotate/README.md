BioR
=====
RAPID, FLEXIBLE SYSTEM FOR GENOMIC ANNOTATION
BIOR (BIOLOGICAL REFERENCE REPOSITORY)


available software
--------
```
htslib-1.2.1
samtools-1.2
bedtools-2.25.0
snpEff_v4_1k
pysam==0.8.3
cava-full-v1.1.1
bior_2.1.1
```


how to build
------------
`docker build --rm -t biodckrdev/bior_annotate 2.1.1/.`


how to download and install
---------------------------
`docker pull biodckrdev/bior_annotate`


how to use
------------
`docker run --rm biodckrdev/bior_annotate <options> <files>`


```
mkdir data

cd data

mkdir references

curl -o references/hg19.fa.gz ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/technical/reference/phase2_reference_assembly_sequence/hs37d5.fa.gz

gunzip references/hg19.fa.gz > references/hg19.fa

docker run -it --rm -v $PWD:/Data biodckrdev/bior_annotate bash

cd /data

samtools faidx references/hg19.fa

sh trunk/bior_annotate.sh -v HG00098.vcf.gz -c catalogFile.docker -d drillFile.docker -T tool_info.minimal.txt -o TEST  -M trunk/config/memory_info.txt -l
```


* Note for windows, you will need to use  
`$ docker run -it --rm -v //c/UserS/m087494/Desktop/bior_annotate:/Data stevenhart/bior_annotate:latest`  

> For this demo, make sure `pwd` contains the following elements

```
Data/  
  references/
    hg19.fa.gz
    hg19.fa.gz.fai

catalogs/
  2015_05_18/
    noTCGA_ExAc.datasource.properties
    noTCGA_ExAc.columns.tsv
    noTCGA_ExAc.tsv.bgz.tbi
    noTCGA_ExAc.tsv.bgz
 ```


software website
----------------
```
http://www.well.ox.ac.uk/cava

https://github.com/Steven-N-Hart/bior_annotate

http://bioinformaticstools.mayo.edu/research/bior/

https://github.com/BioinformaticsToolsAtMayo

https://github.com/Steven-N-Hart/bior_annotate
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
