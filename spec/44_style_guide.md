## Writing

In case of a *specification*, it is important to ask yourself, "Is what I write implementable?" Follow it step by step. Check all the MUSTs and SHOULDs in the normative section.

### Readability
- numbering of paragraphs
- Informative stuff per the section below the normative

### Review and cooperation
Keep stuff in place where it was/is during the review period. When the review period is over, you could
 - relocate sections and paragraphs in the most logical - of best flowing manner

## Technical consistency
 - split the text over markdown files in the spec-up `./spec` folder
 - beware Spec-Up-T has as mandatory directory structure, where the Terms Definition reside in a subdirectory of `./spec` 

## Style guide for Markdown text, headers and anchors

### Conflating transformation

Markdown creates HTML ID attributes from a header. If two identical id's are create, anchors will not work correctly at all times.

Example: 
```text
term 1: “My Awesome Term” and term 2: “My awesome term”
For example:

Original: My Awesome Term
Transformed id: my-awesome-term
```

You cannot definitively reverse my-awesome-term back to "My Awesome Term" because the capitalization and exact spacing are lost.

It should be noted that an HTML document (resulting from Markdown generation) should not contain two identical ID attributes; however, it does not stop browsers from rendering the page.

#### Original Spec-Up feature

This "feature" has been available since the introduction of Spec-Up. It's the responsibility of the text writer to solve conflating anchors.

For terms and definitions, we should introduce a governance rule. 

## Style guide for ToIP terminology

The governance rule we need for terminology:

**a combination of repo and key-formatted term is unique.** Terms should convert to:

<URL>/#term:<term-in-key-format>

for example

https://glossary.trustoverip.org/#term:administering-body

### key-format

In an ecosystem of spec-up-t-based glossaries, there _could be_ another `administering-body` defined somewhere else, for example, `https://github.com/weboftrust/ctwg-main-glossary/#term:administering-body` and this exact same keys are addressable independently via a `tref` and `xref`.


A term that is intended to be generic SHOULD be **lowercase** in the glossary and in the specs and other documents that use that term. 

The key-format is lowercase and dashes: `lowercase-example`

### Proper nouns

To address proper nouns we SHOULD use an alias. 

A key can be uppercase if it is a [[def: ]]. The only exception is an acronym. For example, the following terms are all generic nouns:
- wallet
- agent
- public key (leading to key-format `public-key`)
- key event log (leading to key-format `key-event-log`)

### Forms
Terminology can be defined in various forms: nouns, verbs, adjectives/adverbs, and relations(hips).

#### Example
Noun: Verifier
Verb: Verify
Adjective: verified (signature)
Relationships: verifying

Authors are free to choose any form of a term. However, we highly recommend the use of our key-format (lowercase and dashes for the keys)

It's a way to express their objectives and concepts and give meaning. But use aliases for this. Even multiple forms are welcome, which means that in your scope, you COULD define the noun, the verb, and a relationship. E.g., verifier, verify and verifying.

### Acronym standardization

The following terms are proper nouns or acronyms:
- ToIP
- W3C
- DIF
- X.509
- Diffie-Hellman
- KEL

Good governance Use them as an alias, preferably.

```
[[def: KEL]]

~ See [Key event log](key-event-log)
```

is allowed, but we prefer

```
[[def: key-event-log, Key event log, KEL]]

~ explanation, single point of definition
```

Both definitions will lead to your explanation using

[[ref: KEL]] and via a click to `kel-event-log`

but you'll have to maintain the local reference in markdown, whereas Spec-Up-T will have more abilities to health check refs, trefs and xrefs.

Furthermore,

[[def: key-event-log, Key event log, KEL]]

gives you all these options
```
[[ref: key-event-log]]
[[ref: Key event log]]
[[ref: KEL]]
[[xref: repo, key-event-log]]
[[xref: repo, key-event-log, Key event log]], Showing `Key event log` as the external link text
[[xref: repo, KEL]], Showing `KEL` as the external link text
[[tref: repo, key-event-log]]
[[tref: repo, key-event-log, alias1, <any list of aliases>]]
... being able to reference the tref transclusion with any alias and the key showing `alias1` in local refs.
```


#### Special characters
Notice that the Acronym `X.509` has a special character (`.`). You SHOULD use special characters only if it's crucial for the meaning of the term. 

So, for example, *not this*: `security@hub4issuer` but stick to the guidelines above and define, for example, `security-at-hub-for-issuer`.


#### Constants, variables, and terms in coding
Sometimes, acronyms in code are (partly) in lowercase (e.g., `vLEI`, `eID`, `ind`) for various reasons. One needs to explain those acronyms in terms of concepts and terminology; we allow them to do so in their original case.

#### Authors partly comply and have freedom of choice

### Standardization of acronyms

Two situations:

1. An acronym that is well-known and should be explained/linked to the term it abbreviates. For example, because the acronym is multi-explicable. Example: SCID, TSP.

2. An acronym that is less/hardly known and links to the term it abbreviates

Add 1. A well-known acronym needs its own entry in the glossary:

```Spec-Up-T
[[def: SCID, SCIDs]]

~ [[ref: self-certifying identifier]]
```
If you would only do this:

```Spec-Up-T
[[def: self-certifying identifier, self-certifying identifiers, SCID, SCIDs]]
```

then it's harder to find the entry SCID in the glossary. Referencing SCID In the specification links directly to self-certifying identifier.

Add 2. Less-known acronyms could be defined, but it could burden the glossary with unnecessary entries.

```Spec-Up-T
[[def: LID]]
~ [[ref: legitimized-human-meaningful-identifier]]
```

In this case, it's better to use just one entry:

```Spec-Up-T
[[def: legitimized-human-meaningful-identifier, legitimized human-meaningful identifier, LID, LIDs]]
```

The use of: 

~ Also known as: `[[ref: {acronym or term} ]]`

is in both situations optional.


##### Comply with
- all of the above-mentioned style guides
- the governance of terms using the current terminology source management tools

See the [Roles](roles) section for the various sub roles of an author.