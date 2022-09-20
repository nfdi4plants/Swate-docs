---
layout: docs
title: ISA-JSON import/export
published: 2022-09-19
Author: Kevin Frey
add toc: false
add sidebar: _sidebars\mainSidebar.md
---

We want to offer a group insert of multiple building blocks at once. To do this we transport the information in the form of a process.json file. Which is specified [here](https://isa-specs.readthedocs.io/en/latest/isajson.html#process-schema-json).

# Changed Specifications

To keep these files simple we only use certain fields, which in return are required. The required field are still subject to change (v0.3.0).

```json
{
    "@id": "#process/standard_trypsin_digestion",
    "name": "standard_trypsin_digestion",
    "executesProtocol": {
        "@id": "#protocols/peptide_digestion",
        "name": "peptide_digestion",
    
        "protocolType": {
            "@id": "protein_digestion",
            "annotationValue": "Protein Digestion",
            "termSource": "NCIT",
            "termAccession": "http://purl.obolibrary.org/obo/NCIT_C70845",
            "comments": []
        },
        "description": "The isolated proteins get solubilized. Given protease is added and the solution is heated to a given temperature. After a given amount of time, the digestion is stopped by adding a denaturation agent.",
        "uri": "http://madeUpProtocolWebsize.org/protein_digestion",
        "version": "1.0.0",
        "parameters": [
            {
                "parameterName": {
                  "@id": "protease",
                  "annotationValue": "Peptidase",
                  "termSource": "MS",
                  "termAccession": "http://purl.obolibrary.org/obo/NCIT_C16965",
                  "comments": []
                }
            },
            {
                "parameterName": {
                  "@id": "temperature",
                  "annotationValue": "temperature",
                  "termSource": "Ontobee",
                  "termAccession": "http://purl.obolibrary.org/obo/NCRO_0000029",
                  "comments": []

                }
            },
            {
                "parameterName": {
                    "@id": "time",
                    "annotationValue": "time",
                    "termSource": "EFO",
                    "termAccession": "http://www.ebi.ac.uk/efo/EFO_0000721",
                    "comments": []
                }
            }
        ]
    },
    "parameterValues": [
        {
            "category": {
                "@id": "protease",
                "parameterName": {
                    "@id": "protease",
                    "annotationValue": "Peptidase",
                    "termSource": "MS",
                    "termAccession": "http://purl.obolibrary.org/obo/NCIT_C16965",
                    "comments": []
                }
            },
            "value": {
                "@id": "trypsin",
                "annotationValue": "Trypsin/P",
                "termSource": "NCI",
                "termAccession": "http://purl.obolibrary.org/obo/MS_1001313",
                "comments": []
                
            }
        },
        {
            "category": {
                "@id": "temperature",
                "parameterName": {
                    "@id": "temperature",
                    "annotationValue": "temperature",
                    "termSource": "Ontobee",
                    "termAccession": "http://purl.obolibrary.org/obo/NCRO_0000029",
                    "comments": []

                }
            },
            "value": 37,
            "unit": {
              "@id": "degree_celcius",
              "annotationValue": "degree Celsius",
              "termSource": "UO",
              "termAccession": "http://purl.obolibrary.org/obo/UO_0000027",
              "comments": []
            }
        },
        {
            "category": {
                "@id": "time",
                "parameterName": {
                    "@id": "time",
                    "annotationValue": "time",
                    "termSource": "EFO",
                    "termAccession": "http://www.ebi.ac.uk/efo/EFO_0000721",
                    "comments": []
                }
            },
            "value": 1,
            "unit": {
                "@id": "h",
                "annotationValue": "hour",
                "termSource": "UO",
                "termAccession": "http://purl.obolibrary.org/obo/UO_0000032",
                "comments": []
            }
        }
    ]
}
```

