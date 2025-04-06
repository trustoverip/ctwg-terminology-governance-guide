
## Tools Landscape

Here we present the components and structure of ToIP's concepts, machinery for terminology, and governance.

### git and github

##### Why?
- We need to know who did what
- We need to be able to get back and link to historical (intermediate) result

##### How?
Every role that changes stuff (Create, Update, or Delete) must be on github, and the users sign off their results.

This way:
- sources are GitHub managed, and so is the provenance of each definition
- we can track provenance carefully. Tracking is a step towards fully managed, individually versioned glossary management tooling, such as those developed with Spec-Up-T and KERIDoc, searchable by KERISSE(.org).

### Github landscape

Every group within ToIP that uses Spec-Up has a setup that is more or less like the following. Only WOT-terms combines wiki source management and publication in KERISSE (Still Docusaurus-based, looking into a Spec-Up variant as of Feb 2024).

Platform| Git branch | Software
----: | --------------: | ---------:
github.com repo| main or 'own choice' |Spec-Up
^^  | | VsCode |
^^ | | Node.js / NPM |
github.io pages |gh-pages| `user.github.io/repo` 
^^ |  | github actions |
^^ |  | kerific |
[Infrastructure Terminology Engine ToIP]

### Flow of Writing a Specification in Spec-Up

```mermaid
flowchart TD
 A[Write Spec] --> B[Need to explain term]
 B -->|Can't find!|C[Define]
 B -->|Pick|D[Reference]
 C -->E{Scope?}
 D -->|Grab link|K{Internal?}
 K -->|Yes|A
 K -->|No|F{Add context?}
 E -->|Local|I[spec.md]
 E -->|Central|H[wiki]
 F -->|Local|G[spec.md]
 G --> A
 F --> |No|A 
 H --> |External|J[Reference]
 I --> |Internal ref|J[Reference]
 J --> A
```
### Glossary Flow: Ingest - Curation - Output

![Glossary Flow: Ingest - Curation - Output](https://github.com/henkvancann/terminology-governance-guide/blob/5ecd9e92d75edb3c0844a266537d2d3bbd68676b/images/Darrell-Glossary-Workflow.jpeg?raw=true)

By: Darrell O'Donnell, Jan 2024

### Combining central, external, and internal references to definitions

| TBW : ToIP's position on KERISSE (a superset of terms and concepts documentation) and TEv2? |

ToIP might need both, particularly to onramp organizations that are leveraging ToIP.

What are the components of the following glossary/term/concept toolsets?

- Github (repo, pages and wiki)
- Spec-Up-T
- KERIDoc platform toolset
- TEv2 toolset

What features exist in both, and what is unique in each toolset? If there is overlap, how are they different (e.g., how does an author craft a link from a word in a source document to a term in a specified glossary), and how could they be combined?