# This image belongs to a larger project called Bioinformatics Docker Images Project (http://pegi3s.github.io/dockerfiles)
## (Please note that the original software licenses still apply)

This image facilitates the usage of [SAPP](http://sapp.gitlab.io/), a Semantic genome Annotation Platform with Provenance and designed on the basis of Semantic Web. The platform and corresponding modules allow the user to annotate genomes of various qualities linked to a full chain of data provenance. Resulting is an annotated genome in the `RDF` data model which the user can query and analyse using `SPARQL`. Various modules are available which allow users to compare, annotate and visualise genomes and export annotations to various standard genome annotation formats.

`SAPP` platform includes the following jar packages:

- `Aragorn.jar`
- `BLAST.jar`
- `CRT.jar`
- `Conversion.jar`
- `EnzDP.jar`
- `GenomeInformation.jar`
- `GenomeSync.jar`
- `HDTQuery.jar`
- `HMM.jar`
- `InterProScan.jar`
- `Loader.jar`
- `RDFLoader.jar`
- `TMHMM.jar`
- `Transcriptomics.jar`
- `WoLFPSort.jar`
- `assembly.jar`
- `genecaller.jar`
- `pathwayAnalysis.jar`
- `rnammer.jar`
- `signalp.jar`

To obtain the help of a package, you just need to run:  `docker run --rm pegi3s/sapp java -jar <package.jar> --help` (e.g. `docker run --rm pegi3s/sapp java -jar Conversion.jar --help`)

# SAPP versions and Docker tags

This repository keeps three types of tags:
- `stable-[yyyy.mm.dd]`: images built with the stable jar files in [http://download.systemsbiology.nl/sapp/](http://download.systemsbiology.nl/sapp/).
- `dev-[yyyy.mm.dd]`: images built with the development jar files in [http://download.systemsbiology.nl/sapp/dev](http://download.systemsbiology.nl/sapp/dev).
- `latest`: an image that always points to the most recent `dev-[yyyy.mm.dd]` image.

# Using the SAPP image in Linux
To run a package, you should adapt and run the following command: `docker run --rm -v /your/data/dir:/data pegi3s/sapp java -jar <package.jar> <options>`

In this command, you should replace:
- `/your/data/dir` to point to the directory that contains the input files you want to analyze.
- `<package.jar>` to the name of the `SAPP` package you want to use.
- `<options> ` with the specific options of the `SAPP` package. These options will include the input/output files, which should be referenced under `/data/`.

For instance, to run the `Conversion.jar` package for an Eukaryotic Genome, you should run: `docker run --rm -v /your/data/dir:/data pegi3s/sapp java -jar Conversion.jar -fasta2hdt -input /data/FlyBase_JCLNID.fasta -o /data/DMelanogaster.hdt -genome -chromosome -id DMelanogaster -org "Drosophila melanogaster" -codon 0`

Now you can run `Augustus`, for gene prediction, with the following command:
`docker run --rm -v /your/data/dir:/data pegi3s/sapp java -jar genecaller.jar -augustus -i /data/DMelanogaster.hdt -o /data/DMelanogaster_augustus.hdt -s fly`

# Test data
To test the previous command, the datasets used are available as [FlyBase_JCLNID.fasta](https://github.com/pegi3s/dockerfiles/blob/master/sapp/test_data/FlyBase_JCLNID.fasta) and [DMelanogaster.hdt](https://github.com/pegi3s/dockerfiles/blob/master/sapp/test_data/DMelanogaster.hdt).

# Using the SAPP image in Windows

Please note that data must be under the same drive than the Docker Toolbox installation (usually `C:`) and in a folder with write permissions (e.g. `C:/Users/User_name/`).

As in the Linux case, to run an application, you should adapt and run the following command: `docker run --rm -v "/c/Users/User_name/dir/":/data pegi3s/sapp java -jar <package.jar> <options>`
