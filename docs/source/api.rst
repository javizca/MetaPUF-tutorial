**Overview**
============

This workflow offers the users to integrate publicly available
metagenomics, metatranscriptomics and metaproteomics datasets on PRIDE
and MGnify portals.

+-------------------+-----------------------------+-------------------+
| Software          | Version                     | Purpose           |
+===================+=============================+===================+
| Snakemake         | 7.3.8                       | Wrap the          |
|                   |                             | pipelines         |
+-------------------+-----------------------------+-------------------+
| Sourmash          | 4.4.2                       | Create DNA        |
|                   |                             | sketches to group |
|                   |                             | similar           |
|                   |                             | assemblies        |
|                   |                             | together          |
+-------------------+-----------------------------+-------------------+
| mg-toolkit        | 0.10.1                      | Pull information  |
|                   |                             | from MGify web    |
|                   |                             | portal            |
+-------------------+-----------------------------+-------------------+
| Th                | 1.2.3                       | Convert Thermo    |
| ermoRawFileParser |                             | Raw files into    |
|                   |                             | different formats |
|                   |                             | of spectral       |
|                   |                             | files.            |
+-------------------+-----------------------------+-------------------+
| Mono              | 6.12.0                      | Wrapper around    |
|                   |                             | the .net (C#)     |
|                   |                             | ThermoFisher      |
|                   |                             | Th                |
|                   |                             | ermoRawFileReader |
|                   |                             | library for       |
|                   |                             | running on Linux  |
+-------------------+-----------------------------+-------------------+
| SearchGUI         | 4.0.41                      | Combine multiple  |
|                   |                             | search engines to |
|                   |                             | perform peptide   |
|                   |                             | identification    |
|                   |                             | from a protein    |
|                   |                             | sequence          |
|                   |                             | database.         |
+-------------------+-----------------------------+-------------------+
| PeptideShaker     | 2.0.33                      | Interpret         |
|                   |                             | proteomics        |
|                   |                             | identification    |
|                   |                             | results from      |
|                   |                             | multiple search   |
|                   |                             | and generate      |
|                   |                             | peptide and       |
|                   |                             | protein reports.  |
+-------------------+-----------------------------+-------------------+

The workflow is defined in snakemake and is available at `link to
github <https://github.com/PRIDE-reanalysis/MetaPUF.git>`__

**Workflow**
============

The sankemake workflow consists of three modules.

-  Generating protein sequence database/(s)

-  Mass-spectrometry based metaproteomics analysis

-  integrating multi-omics information and visualisation on the MGnify
   web portal

`MetaPUF
workflow <https://docs.google.com/presentation/d/1OIA4IHKQ8kE5WYTUXbCrVJvpGlPyx9SBQ5iZi5gURHg/edit#slide=id.g1529e8a0fb5_0_0>`__
