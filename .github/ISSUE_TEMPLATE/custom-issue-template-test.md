---
name: Custom issue template test
about: Describe this issue template's purpose here.
title: ''
labels: ''
assignees: ''

---

name: Add a new SPARQL query
description: Submit a new SPARQL query with context, hints, and metadata
title: "[Query] "
labels: [query, enhancement]
body:
  - type: input
    id: query-name
    attributes:
      label: Query Name
      description: A short, descriptive title (3–8 words)
      placeholder: e.g. Find diseases with genetic causes
    validations:
      required: true

  - type: textarea
    id: description
    attributes:
      label: What does this query do?
      description: Describe the purpose of the query in a few lines.
      placeholder: |
        This query retrieves all diseases annotated with genetic causes from the Orphanet dataset.
    validations:
      required: true

  - type: dropdown
    id: difficulty
    attributes:
      label: Difficulty
      description: How hard is it to write or understand this query?
      options:
        - Beginner
        - Intermediate
        - Advanced
    validations:
      required: false

  - type: dropdown
    id: ontology
    attributes:
      label: Ontology used
      description: Which ontology or dataset does this query rely on?
      options:
        - Orphanet
        - HOOM
        - FERDO
        - Other
    validations:
      required: false

  - type: textarea
    id: context
    attributes:
      label: Context (optional)
      description: Why and where is this query useful? Project, data source, etc.
      placeholder: |
        Used in the FERDO project to analyze mappings between genetic annotations.

  - type: textarea
    id: hints
    attributes:
      label: Hints or Steps (optional)
      description: List optional hints or steps to solve the query (1 per line)
      placeholder: |
        - Use the `rdfs:subClassOf` hierarchy
        - Filter by `obo:GENO_0000000` type

  - type: textarea
    id: sparql
    attributes:
      label: SPARQL Query (with PREFIX)
      description: Paste the full SPARQL query with all necessary PREFIX declarations.
      placeholder: |
        PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
        PREFIX obo: <http://purl.obolibrary.org/obo/>

        SELECT ?disease ?label
        WHERE {
          ?disease a obo:ORDO_0000000 ;
                   rdfs:label ?label .
        }
    validations:
      required: true

  - type: textarea
    id: rdf-result
    attributes:
      label: Sample RDF Result (optional)
      description: Provide a small example of expected RDF output (Turtle, RDF/XML or JSON-LD).
      placeholder: |
        @prefix obo: <http://purl.obolibrary.org/obo/> .
        obo:ORDO_123456 a obo:ORDO_0000000 ;
          rdfs:label "Example disease" .
