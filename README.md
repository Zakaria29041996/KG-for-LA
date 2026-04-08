# Knowledge Graph for Learning Analytics from xAPI Data

## Overview

This project focuses on building a **data engineering pipeline** to transform raw xAPI data into a semantically enriched knowledge graph for learning analytics.

The SMART team at the University of Liège collects fine-grained student interaction data through the FB4You mobile application using the Experience API (xAPI). While xAPI standardizes data collection, the resulting datasets are semi-structured, heterogeneous, and difficult to analyze without complex queries and strong domain knowledge.

This project addresses these challenges by converting raw JSON xAPI statements into a structured, interoperable, and queryable knowledge graph.

---

## Approach

* Analyzed over 2,100 heterogeneous xAPI JSON files
* Identified implicit relationships, inconsistencies, and undocumented conventions
* Designed **PROV-EXT**, an extension of the PROV-O ontology
* Implemented RDF mappings using RML
* Built a knowledge graph containing over **1.3 million RDF triples**

---

## Data Engineering Pipeline

```text
xAPI JSON → Apache Drill → RML (BURP) → RDF Knowledge Graph (N-Quads)
```

---

## Key Features

* End-to-end data pipeline for semi-structured data transformation
* Schema-on-read querying using Apache Drill
* Semantic enrichment via ontology design (PROV-EXT)
* Support for complex analytical and semantic queries

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
* Enabled intuitive exploration of learning behaviors

---

## Tech Stack

* Apache Drill
* RML mappings
* BURP
* RDF / N-Quads
* PROV-O + PROV-EXT ontology

---

## Data Availability

Due to **GDPR (General Data Protection Regulation)** constraints, the original datasets and the generated knowledge graph cannot be publicly shared.

However, this repository provides:

* Mapping configurations
* Pipeline setup instructions
* Example queries

to allow reproducibility on similar xAPI datasets.

---

## Future Work

* Ontology enrichment
* Scalability improvements
* Data quality validation
* User-friendly interfaces for non-technical users

---

## Context

This project was developed as part of research on learning analytics at the University of Liège.
