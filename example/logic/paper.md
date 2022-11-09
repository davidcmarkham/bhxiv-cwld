---
title: 'Colloquial language mappings to ontologies for wet lab biology'
title_short: 'CWLD'
tags:
  - ontologies
authors:
  - name: David Markham
    orcid: 0000-0001-7765-369X
    affiliation: 1
  - name: James McLaughlin
    orcid: 0000-0002-8361-2795
    affiliation: 2
affiliations:
  - name: Newcastle University, Newcastle-upon-Tyne, UK
    index: 1
  - name: EMBL-EBI, Hinxton, Cambridge, UK
    index: 2
date: 12 November 2022
cito-bibliography: paper.bib
event: BioHackathon Europe 2022
biohackathon_name: "NBDC/DBCLS BioHackathon"
biohackathon_url:   "http://2019.biohackathon.org/"
biohackathon_location: "Paris, France, 2022"
group: Logic programming group
# URL to project git repo --- should contain the actual paper.md:
git_url: https://github.com/biohackrxiv/bhxiv-gen-pdf
# This is the short authors description that is used at the
# bottom of the generated paper (typically the first two authors):
authors_short: David Markham & James McLaughlin

---


<!--

The paper.md, bibtex and figure file can be found in this repo:

  https://github.com/journal-of-research-objects/Example-BioHackrXiv-Paper

To modify, please clone the repo. You can generate PDF of the paper by
pasting above link (or yours) in

  http://biohackrxiv.genenetwork.org/

-->

# Introduction

The use of ontology terms can make data more FAIR and tractable by machines. However, the highly formalised terminology used by these ontology terms does not always match the colloquial language used by practitioners. This disparity can (a) make it difficult for practitioners to understand the language used by knowledge stored in ontologies; and (b) make it difficult to machine-interpret information written by practitioners to map it to ontologies.

This problem is particularly relevant in the ELIXIR Microbial Biotechnology community, as although the domain has adopted ontologies and data standards such as SO, SBO, GO, and SBOL for data representation, the tools developed often use ontology terms directly rather than the language used in the wet lab (i.e. by the people using the tools.)

At the BioHackathon 2022 in Paris, France, we initiated an effort to address this problem by (a) mining the internet for colloquial language used by biologists, (b) constructing a dictionary of this language and its mappings to ontology terms, and (3) constructing a recommendation table of terminology for MB tool developers based on this data.

While initially developed to serve the MB community, we hope that the dictionary will serve as a helpful resource for anyone hoping to map from colloquial wet lab language to ontology terms for e.g. text mining applications.

# Using Stack Exchange to gather colloquial domain language

Replace below with word cloud png
![Logic programming resolver traverses the solution space to find all matches \label{fig}](./logic-programming.png)

![An SVG example](./test.svg)

# Creating a dictionary of colloquial wet lab terminology

An issue we encountered in making the dictionary available is that there is no standard/FAIR data format to publish string to term mappings. The SSSOM (Super Simple Standard for Ontology Mappings) supports term to term mappings, but not string to term. We have discussed with the SSSOM developers about implementing support for this, and are helping with a pull request to add it to the standard. We will then hopefully be able to publish the dictionary in the future using SSSOM.







# Terminology recommendations for Microbial Biotechnology tool developers
This list is non-exhaustive, but covers a selection of terms that we noticed differ between MB tools.


<table>
  <thead>
    <th>Term</th>
    <th>MB tools/ontologies using this term</th>
    <th>Frequency on Biology Stack Exchange</th>
  </thead>
  <tbody>
    <tr>
      <td>Component</td>
      <td>SBOL, SBOLDesigner, SBOLCanvas</td>
      <td>2163</td>
    </tr>
    <tr>
      <td>Module</td>
      <td>SBOL</td>
      <td>311</td>
    </tr>
    <tr>
      <td>Device</td>
      <td></td>
      <td>677</td>
    </tr>
    <tr>
      <td>System</td>
      <td></td>
      <td>16098</td>
    </tr>
    <tr>
      <td>Ribosome Entry Site</td>
      <td>SO</td>
      <td>8</td>
    </tr>
    <tr>
      <td>RBS</td>
      <td></td>
      <td>548</td>
    </tr>
    <tr>
      <td>Upregulation</td>
      <td></td>
      <td>79</td>
    </tr>
    <tr>
      <td>Downregulation</td>
      <td></td>
      <td>91</td>
    </tr>
  </tbody>
  </table>

# Availability

The dictionary is available in CSV format at 

# Future work


We have used the Stack Exchange dataset to analyse the popularity of a small set of terms used in MB which differ between different tools. The next step would be to apply this to entire ontologies, annotating every label and synonym in the ontology with its popularity. This information could then be used to inform whether the primary label of the term should be preferred, or whether a synonym should be preferred instead.

It would also be interesting to explore how the Stack Exchange datasets can be used to gather domain-specific language for different domains, using a similar approach subtracting “meta” terms and analysing the delta. There are 98 Stack Exchange sites at the time of writing.

We intend to publish the dictionary using SSSOM, once the ability to map strings to terms has been implemented.

















<!--
# Results
-->

## Research of state-of-the-art logic programming facilities for SPARQL

The working group researched current solutions for combining logic
programming with SPARQL.
[ClioPatria](http://www.semantic-web-journal.net/system/files/swj1074.pdf)
is an in-memory RDF quad-store tightly coupled with SWI-Prolog by Jan
Wielemaker, the main author of SWI-Prolog
[@WielemakerBHO15]. SWI-Prolog is published under a BSD license, and
there even exist bindings for
[ClioPatria and Python](http://wi.hwtk.de/WLP2018/Papers/WLP_2018_paper_4.pdf),
for example, although we were unable to locate the source code. We
think ClioPatria and SWI-Prolog are particularly useful for teaching,
and for (in-memory) semantic web applications. SWI-Prolog comes with
client libraries for SQL and SPARQL queries.

## Accessing biological databases using SPARQLProg

<!--
    State the problem you worked on
    Give the state-of-the art/plan
    Describe what you have done/results starting with The working group created...
    Write a conclusion
    Write up any future work
-->

A number of biological databases make their data available in RDF
format, supporting SPARQL access---for example,
[Uniprot](https://www.uniprot.org/),
[NCBI Pubchem](https://pubchemdocs.ncbi.nlm.nih.gov/rdf) and the
[EBI RDF platform](https://www.ebi.ac.uk/rdf/).
SPARQL provides a subset of what logic programming can do.
However, SPARQL queries lack the property of composability and there is no way to
reuse modular components across queries.  For example, to execute a
range query on a genomic region using the FALDO model [@agreesWith:Bolleman2016]
requires authoring a complex query over many triples. If we then wish
to reuse parts of that query in a more complex query, we have to
manually compose them together.

The working group added codes to
[SPARQLProg](https://github.com/cmungall/sparqlprog) which provides a
way to define modular query components using logic programming.
SPARQLProg is written in
SWI-Prolog and has a Python interface library. All code has been made
available in the example directory of
SPARQLProg which provides
sophisticated mapping of logic queries to SPARQL.

For example, a 4-part predicate `feature_in_range` can be composed
with a binary \
`has_mouse_ortholog` predicate:

```
    feature_in_range(grch38:"X", 10000000, 20000000, HumanGene),
    has_mouse_ortholog(HumanGene, MouseGene)
```

This will compile down to a more complex SPARQL query, and execute it against a remote endpoint.

SPARQLProg now includes bindings for many common biological SPARQL
endpoints. As part of this hackathon we developed codes to access RDF
databases of MBGD [@Chiba2015], KEGG OC, TogoVar, JCM, Allie, EBI
 BioSamples, UniProt, and DisGeNET [@Queralt2016]. Future work includes using these
Prolog codes as building blocks for integrative analysis.

## Extending the Biolink Model

<!--
    State the problem you worked on
    Give the state-of-the art/plan
    Describe what you have done/results starting with The working group created...
    Write a conclusion
    Write up any future work
-->

The [Biolink Model](https://github.com/biolink/biolink-model) (see
above) is a data model developed for representing biological and
biomedical knowledge. It includes a schema and generated objects for
the data model and upper ontology. The BioLink Model was designed with
the goal of standardizing the way information is represented in a
graph store, regardless of the formalism used. The working group
focused on extending this model to support representation of a wide
variety of knowledge.

The following tasks were accomplished as part of the BioHackathon:

\begin{enumerate}
\item Represent datasets and their related metadata
\item Represent family and pedigree information to support clinical knowledge
\item Make the provenance model more rich and descriptive
\end{enumerate}

For future work, the group will ensure that the new classes added to
the model will have appropriate mappings to other schemas and
ontologies.

##  Relational Biolink type inference for mediKanren

<!--
    State the problem you worked on
    Give the state-of-the art/plan
    Describe what you have done/results starting with The working group created...
    Write a conclusion
    Write up any future work

* Remote member Nada Amin, Chris Mungall, Deepak Unni, Will Byrd

-->

miniKanren is an embedded Domain Specific Language for logic
programming.  The goal was to implement a relational type inferencer
for the [Biolink Model](https://biolink.github.io/biolink-model/) in
miniKanren, which can be integrated into mediKanren. The working group
added a `yaml` subdirectory to the mediKanren GitHub page, and created
multiple files in https://github.com/webyrd/mediKanren/yaml where
`yaml2sexp.py` generates the `biolink.scm` file which contains an
s-expression version of the Biolink yaml file. `yaml.scm` contains
miniKanren relations, and Chez Scheme code that generates miniKanren
relations based on `biolink.scm`. These are giant miniKanren `conde`
clauses that can be thought of as relational tables.  `yaml.scm` also
contains tests for the relations.

Future work includes:

1. integrating this work into the Racket mediKanren code;
2. integrating with the data categories in the KGs;
3. and creating query editor with decent type error messages, autocompletion,
   query synthesis, etc.

# Discussion

The working group concluded that there is ample scope for logic
programming in bioinformatics. Future work includes expansion of
accessing semantic web databases using SPARQLProg, expanding the
BioLink model, and adding dynamic SPARQL support to miniKanren.

## Acknowledgements

We thank the organizers of the NBDC/DBCLS BioHackathon 2019 for
travel support for some of the authors.

## References
