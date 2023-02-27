**Tutorial**
=============

Below you can find a tutorial on how to use some of the MetaPUF
pipelines. This gives you a flavor of what can be achieved using the MetaPUF pipelines.

**Installation**
----------------

From Bioconda
~~~~~~~~~~~~~

The pipelines in MetaPUF rely on third party software such as Snakemake
or mg-toolkit that are not Python libraries. We therefore recommend to
use conda, which provides pre-compiled software for you.

Install conda executable
^^^^^^^^^^^^^^^^^^^^^^^^

We recommend to install Miniconda Python3 distribution from
`Download <https://conda.io/en/latest/miniconda.html>`__.

Add Bioconda channels
^^^^^^^^^^^^^^^^^^^^^

When you want to install a ny package, conda looks on the official
Anaconda website (channel). However we will make
use of the Bioconda channel. To use this type the command:

::

   conda config --add channels defaults
   conda config --add channels bioconda

It is important to have the channels in the right order. You can check
the `order <https://bioconda.github.io/>`__ with the command

::

   conda config --get channels

Create a conda environment
^^^^^^^^^^^^^^^^^^^^^^^^^^

Once miniconda is installed and the channels set, you can create a new
environment for MetaPUF using the command

::

   conda env --name metapuf create --f metapuf_env.yml

You must activate the 'metapuf' environment whenever you work using this
workflow.

::

   conda activate metapuf

From Github source code
~~~~~~~~~~~~~~~~~~~~~~~

You can also install metapuf locally from Github

::

   conda env --name metapuf create --f metapuf_env.yml
   conda activate metapuf
   git clone https://github.com/PRIDE-reanalysis/MetaPUF.git
   cd MetaPUF

**Inputs**
----------

The workflow requires the following inputs in the config.yaml file:

-  ``Study: (ERP124921) | input_dir: Absolute path to the input directory``

This parameter takes in European Nucleotide Archive (ENA) secondary
study accession numbers: starts with (ERP|DRP|SRP) followed by six digits.

You can also input your own metagenomics and/or metatranscriptomics
assemblies and metaproteomics data from the same samples. There are some
instructions regarding the naming conventions to follow:

-  Assembly files should have file names ending with ““.

-  The workflow accepts protein predicted from Prodigal.

-  The protein file names should end with ““.

-  ``Pride_id: PRIDE dataset accession For example (PXD005780)``

Depending on the network, it is better to download the metaproteomics dataset (Mass
Spectrometry raw files) beforehand and put them in the correct folder, each sample should
have a sub-folder for the Raw files. You can also use the pipeline to
download the files, but it may take time. Also, if the
connection fails, all the files will need to be re-downloaded again.

\*\* Example of folder structrure: (PXD005780 for example) Under the root
path of the MetaPUF project, create a folder named ``input/Raw``, under
this path, you need to create sub-folders for each sample: ``S06``,
``S07``, … etc. And one should put the raw files into the correlated sub-folder. If
there are multiple raw files for one sample, please put all those raw
files into the same sub-folder which represents for one sample.

-  ``Version: The version of MGnify analysis.``

This accepts either “4.1” or “5.0” as string values. The default is
“5.0”. \* ``Db_size: Size of the proteins sequence database in bytes.``

The default is 1073741824 (integer data type). \*
``outputdir: Directory path to save the output``

The user needs to enter a .csv file that contains all the sample
information as shown in the example below

+--------+------------+------------+------------+------------+--------+
| Sample | PRIDE      | Raw file   | Raw file   | Sample     | As     |
|        | Accession  |            | URLs       | Accession  | sembly |
+========+============+============+============+============+========+
| S6     | PXD005780  | S6.raw     | h          | ERS1509315 | ERZ1   |
|        |            |            | ttps://ftp |            | 669330 |
|        |            |            | .pride.ebi |            |        |
|        |            |            | .ac.uk/pri |            |        |
|        |            |            | de/data/ar |            |        |
|        |            |            | chive/2017 |            |        |
|        |            |            | /07/PXD005 |            |        |
|        |            |            | 780/S6.raw |            |        |
+--------+------------+------------+------------+------------+--------+

This workflow looks for this file in the config directory. You don’t
need to provide the ``PRIDE Accession`` number and ``Raw file URLs`` if
you have already the data available locally, and just leave the column as 
blank, however the header is still needed.

**Quick start**
---------------

Snakemake dry run command

::

   Snakemake -n --cores 4

To run the workflow with Snakemake

::

   Snakemake --cores 4

**Outputs**
-----------

The outputs include the following files \* ``Protein sequence database``

-  ``Report informing assemblies in each protein sequence db``

-  ``Protein reports from PeptideShaker``

-  ``Peptide report from PeptideShaker``

-  ``Post-processing reports``

-  ``High confidence GFF format report``

-  ``Low confidence GFF format report``
