---
title: 'CWLD: Mapping colloquial wet lab language to ontologies'
title_short: 'CWLD'
tags:
  - ontologies
  - mappings
  - microbialbiotechnology
  - bioengineering
  - syntheticbiology
  - datamining
  - based
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
biohackathon_name: "BioHackathon Europe 2022"
biohackathon_url:   "http://biohackathon-europe.org/"
biohackathon_location: "Paris, France, 2022"
group: Project 14
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

## List of Abbreviations
CSV - Comma Separated Values; FAIR - Findable, Accessible, Interoperable and Reusable; GO - Gene Ontology; MB - Microbial Biotechnology; RBS - Ribosome Binding Site; SBO - Systems Biology Ontology; SBOL - Synthetic Biology Open Language; SE - Stack Exchange; SO - Sequence Ontology; SSSOM - Super Simple Standard for Ontology Mappings; XML - eXtensible Markup Language

# Introduction

The use of ontology terms can make data more FAIR and tractable by machines. However, the highly formalised terminology used by these ontology terms does not always match the colloquial language used by practitioners. This disparity can (a) make it difficult for practitioners to understand the language used by knowledge stored in ontologies; and (b) make it difficult to machine-interpret information written by practitioners to map it to ontologies.

This problem is particularly relevant in the ELIXIR Microbial Biotechnology (MB) community, as although the domain has adopted ontologies and data standards such as SO [@eilbeck2005sequence], SBO [@courtot2011controlled], GO [@gene2004gene], and SBOL [@galdzicki2014synthetic] for data representation, the tools developed often use ontology terms directly rather than the language used in the wet lab (i.e. by the people using the tools.)


# Results


At the [BioHackathon](https://biohackathon-europe.org) 2022 in Paris, France, we initiated an effort to address this problem by (a) mining the internet for colloquial language used by biologists; (b) constructing a dictionary (_CWLD: colloquial wet lab dictionary_) of this language and its mappings to ontology terms; and (c) constructing a table of the occurrences of different terminology used in MB tools and resources.

While initially developed to serve the MB community, we hope that the dictionary will serve as a helpful resource for anyone hoping to map from colloquial wet lab language to ontology terms for e.g. text mining applications.

## Using Stack Exchange to gather colloquial domain language

Biology Stack Exchange is a forum where colloquial language is used to ask and answer questions throughout the biology domain. We took the data available at [archive.org/download/stackexchange](https://archive.org/download/stackexchange) and extracted the words in the posts and comments to count up the frequency in which each word is used. To remove commonly used words and words that are non-specific to biology, we performed the same exercise on Meta Stack Exchange and subtracted the most commonly used words on the Meta dataset from the Biology dataset. This resulted in a set of words that were commonly used on the Biology Stack Exchange and the frequency in which each word appeared. We used this to generate a wordcloud.

![Most commonly used words on Biology SE. The 1000 most frequently used words in the Meta SE dataset were removed from the Biology SE dataset. The Meta SE dataset contained the first 100000 records for Posts and the same for Comments; the records on archive.org were updated on 08-Oct-2022 10:24 and 08-Oct-2022 00:47 for Meta SE and Biology SE respectively.](./wordcloud.png)

## Creating a dictionary of colloquial wet lab terminology
 
We used a combination of information gathered by talking to wet lab biologists at the BioHackathon, and wordclouds generated from the Biology Stack Exchange dataset, to generate a dictionary of colloquial wet lab biology language, which we have named CWLD (pronounced \emph{quilled}): Colloquial Wet Lab Dictionary.

One of the important considerations was that the same term can have different meanings depending on the domain. For example, _transformation_ to a microbiologist means transferring genetic material into a cell, while for a human biologist it means converting a cell to an immortal phenotype that divides infinitely. We therefore defined an initial set of domains we were interested in to categorise the terms. We also mapped these domains to the EDAM ontology and the FAIRsharing subject ontology (SRAO), where possible.

\begin{figure}
\begin{tabular}{ |p{3cm}|p{6cm}|p{6cm}| } 
\hline
\rowcolor{gray}
\textbf{Domain} & \textbf{EDAM} & \textbf{SRAO} \\
\hline
Microbiology & \texttt{http://edamontology.org/topic\_3301} & \texttt{NCIT:C16851} \\
\hline
Molecular Biology & \texttt{http://edamontology.org/topic\_3047} & \texttt{http://edamontology.org/topic\_3047} \\
\hline
Plant Biology & \texttt{http://edamontology.org/topic\_0780} & \\
\hline
Biochemistry & \texttt{http://edamontology.org/topic\_3292} & \texttt{http://edamontology.org/topic\_3292} \\
\hline
Cell Biology & \texttt{http://edamontology.org/topic\_2229} & \texttt{NCIT:C17992} \\
\hline
Synthetic Biology & \texttt{http://edamontology.org/topic\_3895} & \texttt{OMIT:0027298} \\
\hline
\end{tabular}
\caption{Domains used by terms in CWLD and their mapping to EDAM.}
\end{figure}

By the end of the BioHackathon, CWLD had 104 terms. As an example, the table below shows a small example excerpt of these terms and how they map to ontology terms.
  
  
\begin{figure}
\begin{tabular}{ |p{1.8cm}|p{1.62cm}|p{3cm}|p{2.4cm}|p{3cm}| }
\hline  
\rowcolor{gray}
\textbf{Name} & \textbf{Domain} & \textbf{Description} & \textbf{Mapping} & \textbf{Wikipedia} \\
\hline  
Silencing & Biology & Inhibiting the expression of a gene & \texttt{GO:0010629} \emph{negative regulation of gene expression} & \url{https://en.wikipedia.org/wiki/Gene_silencing} \\
\hline  
Transform & Molecular Biology & Transferring genetic material into a cell. Typically, uptake of a plasmid into a cell or population of cells. & \texttt{EFO:0000726} \emph{transfection} & \url{https://en.wikipedia.org/wiki/Transformation\_(genetics)} \\
\hline  
RBS & Molecular Biology & Sequence that a ribosome recognises and attaches at to initiate translation & \texttt{SO:0000139} \emph{ribsome entry site} & \url{https://en.wikipedia.org/wiki/Ribosome-binding\_site} \\
\hline  
Restriction Site & Molecular Biology & The recognition sequence of a specific restriction enzyme & \texttt{SO:0001687} \emph{restriction enzyme recognition site} & \url{https://en.wikipedia.org/wiki/Restriction\_site} \\
\hline  
Digestion & Molecular Biology & Using a restriction enzyme to cut a DNA sequence at a specific location (a restriction site) & \texttt{GO:0015666} \emph{restriction endodeoxyribonuclease activity} & \url{https://en.wikipedia.org/wiki/Restriction\_digest} \\
\hline  
Plate \emph{(verb)} & Microbiology & Put cells on solid media for growing & N/A & \url{https://en.wikipedia.org/wiki/Inoculation} \\
\hline  
Plate \emph{(noun)} & Microbiology & Labware containing solid growth media & N/A & \url{https://en.wikipedia.org/wiki/Petri\_dish} \\
\hline  
Downregulate & Molecular Biology & Negatively influence gene expression & \texttt{GO:0010629} \emph{negative regulation of gene expression} & \url{https://en.wikipedia.org/wiki/Downregulation\_and\_upregulation} \\
\hline  
Upregulate & Molecular Biology & Positively influence gene expression & \texttt{GO:0010628} \emph{positive regulation of gene expression} & \url{https://en.wikipedia.org/wiki/Downregulation\_and\_upregulation} \\
\hline
\end{tabular}
\caption{A small excerpt of terms in CWLD and their mappings. The complete dictionary has 104 terms as of the end of the BioHackathon.}
\end{figure}

### Publishing String to Term Mappings
  
One issue we encountered in making the dictionary available is that there is no standard/FAIR data format to publish string to term mappings. The SSSOM (Super Simple Standard for Ontology Mappings) [@matentzoglu2022simple] supports term to term mappings, but not string to term. We have discussed with the SSSOM developers about implementing support for this, and are helping with a pull request (https://github.com/mapping-commons/sssom/pull/235) to add it to the standard. We will then hopefully be able to publish the dictionary in the future using SSSOM.

# Terminology in Microbial Biotechnology tools & resources

Using the Stack Exchange dataset, we also analysed the popularity of terms used in MB tools and resources to establish which terms are more commonly used. This list is non-exhaustive, but covers a selection of terms that we noticed differ between MB tools such as SBOLDesigner [@zhang2017sboldesigner] and SBOLCanvas [@terry2021sbolcanvas].


\begin{figure}
\begin{tabular}{ |p{3cm}|p{3cm}|p{3cm}|p{3cm}| }
\hline  
\rowcolor{gray}
\textbf{Term} & \textbf{MB tools/ontologies using this term} & \textbf{Frequency on Biology Stack Exchange} & \textbf{Search Term} \\
\hline  
Part & iGEM & 9065 & part + parts \\
\hline  
\rowcolor{lightgray}
Component           & SBOL, SBOLDesigner, SBOLCanvas      & 2163                                & component           \\
\hline  
\rowcolor{lightgray}
Module              & SBOL                                & 311                                 & module              \\
\hline  
\rowcolor{lightgray}
Device              &                                     & 677                                 & device              \\
\hline  
\rowcolor{lightgray}
System              &                                     & 16098                               & system              \\
\hline  
\rowcolor{white}
RBS                 &                                     & 548                                 & rbs                 \\
\hline  
\rowcolor{white}
Ribosome Entry Site & SO                                  & 8                                   & ribosome entry site \\
\hline  
\rowcolor{lightgray}
Restriction Enzyme Recognition Site & SO & 0 & restriction enzyme recognition site \\
\hline  
\rowcolor{lightgray}
RERS & SBOLCanvas & 0 & rers \\
\hline  
\rowcolor{lightgray}
Restriction Site & & 52 & restriction site \\
\hline  
\rowcolor{white}
Upregulation        &                                     & 216                                 & upreg*              \\
\hline  
\rowcolor{white}
Stimulation & SBO, SBOLCanvas & 1666 & stimulat* \\
\hline  
\rowcolor{white}
Positive Regulation & GO & 17 & positive reg* + positively reg* \\
\hline  
\rowcolor{lightgray}
Downregulation      &                                     & 195                                 & downreg*            \\
\hline  
\rowcolor{lightgray}
Inhibition & SBO, SBOLCanvas & 3879 & inhibit* \\
\hline  
\rowcolor{lightgray}
Negative Regulation & GO                                  & 36                                  & negative reg* + negatively reg* \\
\hline  
\rowcolor{white}
Role & SBOLDesigner & 2068 & role \\
\hline  
\rowcolor{white}
Function & & 3567 & function \\
\hline  
\rowcolor{lightgray}
Backbone & SBOLCanvas & 444 & backbone \\
\hline  
\rowcolor{lightgray}
Vector & & 1608 & vector \\
\hline  
\rowcolor{lightgray}
Plasmid & & 3026 & plasmid \\
\hline  
\rowcolor{white}
Host & & 2507 & host + hosts \\
\hline  
\rowcolor{white}
Chassis & & 3 & chassis + châssis \\
\hline
\end{tabular}
\caption{A selection of terms used in MB that differ between tools, and their respective frequency in the Biology Stack Exchange dataset.}
\end{figure}


<!-- ![Table 1 - TEST]
  A table Caption here would be delightful, how do we do this?
-->

This data was collected by searching for strings within the Posts and Comments XML files (ignoring case sensitivity). There are issues with this methodology due to variations or typos in the way that this language may be used. Additionally, if punctuation was used before or after the word, it may not be included in the result due to the insertion of spaces in our search terms to account for prefixes and suffixes. This data is also prone to a lack of context. For example, the term "system" may be used in Engineering Biology to mean a genetic circuit but "system" is commonly used for other meanings. In future, a more robust approach could be used, but this data provides an initial investigation into the use of some choice terminology.


# Availability

The dictionary is available in CSV format at https://github.com/davidcmarkham/cwld.

# Future work

* **Informing ontologies:** We have used the Stack Exchange dataset to analyse the popularity of a small set of terms used in MB which differ between different tools. The next step would be to apply this to entire ontologies, annotating every label and synonym in the ontology with its popularity. This information could then be used to inform whether the primary label of the term should be preferred, or whether a synonym should be preferred instead.

* **Application to other domains:** It would also be interesting to explore how the Stack Exchange datasets can be used to gather domain-specific language for different domains, using a similar approach subtracting “meta” terms and analysing the delta. There are 98 Stack Exchange sites at the time of writing.

* **FAIR publication of CWLD:** We intend to publish the dictionary using SSSOM, once the ability to map strings to terms has been implemented. This will allow it to be used with any tooling that supports SSSOM, without any specific code being added for CWLD.

## Acknowledgements

With thanks to ELIXIR and the organisers of BioHackathon Europe for providing an excellent environment to conduct this work, and for funding the travel arrangements of the authors.

## References
