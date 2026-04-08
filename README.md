# Knowledge Graph for Learning Analytics from xAPI Data

## Overview

This project aims to improve learning analytics by transforming raw xAPI data into a semantically enriched knowledge graph.

The SMART team at the University of Liège collects fine-grained student interaction data through the FB4You mobile application using the Experience API (xAPI). While xAPI standardizes data collection, the resulting datasets are semi-structured, heterogeneous, and difficult to analyze without complex queries and strong domain knowledge.

This project addresses these challenges by converting raw JSON xAPI statements into a structured and queryable knowledge graph.

---

## Approach

* Analyzed over 2,100 heterogeneous xAPI JSON files
* Identified implicit relationships, inconsistencies, and undocumented conventions
* Designed **PROV-EXT**, an extension of the PROV-O ontology
* Implemented RDF mappings using RML
* Built a knowledge graph containing over **1.3 million RDF triples**

---

## Pipeline

```text
xAPI JSON → Apache Drill → RML (BURP) → RDF Knowledge Graph 
```

---

## Key Features

* Transformation of semi-structured JSON into semantically rich RDF data
* Schema-on-read querying using Apache Drill
* Semantic interoperability through ontology design (PROV-EXT)
* Support for advanced analytical queries

---

## Use Cases

The knowledge graph enables:

* Student activity timeline reconstruction
* Performance correlation analysis
* Behavioral pattern discovery and clustering

---

## Results

* Improved data interpretability compared to raw JSON
* Simplified complex analytical queries
* Enabled more intuitive exploration of learning behaviors

---

## Tech Stack

* Apache Drill (SQL over JSON)
* RML mappings
* BURP (mapping execution)
* RDF / N-Quads
* PROV-O + PROV-EXT ontology

---

## Future Work

* Ontology enrichment
* Scalability improvements
* Data quality validation
* User-friendly interfaces for non-technical users

---

## Context

This project was developed in the context of research on learning analytics at the University of Liège.
