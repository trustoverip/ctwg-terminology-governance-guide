## Writing

In case of a *specification*, it is important to ask yourself, "Is what I write implementable?" Follow it step by step. Check all the MUSTs and SHOULDs in the normative section.

### Readability
- numbering of paragraphs
- Informative stuff per the section below the normative

### Review and cooperation
Keep stuff in place where it was/is during the review period. When the review period is over, you could
 - relocate sections and paragraphs in the most logical - of best flowing manner
 - split the text over markdown files in the spec-up `./spec` folder


## Style guide for ToIP terminology

A term that is intended to be generic SHOULD be **lowercase** in the glossary and in the specs and other documents that use that term. A term SHOULD only be uppercase if it is a [[def: proper noun]]. The only exception is an acronym. For example, the following terms are all generic nouns:
- wallet
- agent
- public key (and public-key)
- key event log (and key-event-log)

### Transform spaces to dashes

| TBW : see guideline ToIP by Daniel Hardman for the wiki markdown-files|


### Forms
Terminology can be defined in various forms: nouns, verbs, adjectives/adverbs, and relations(hips).

#### Example
Noun: Verifier
Verb: Verify
Adjective: verified (signature)
Relationships: verifying

Authors are free to choose any form of a term. It's a way to express their objectives and concepts and give meaning. Even multiple forms are welcome, which means that in your scope, you COULD define the noun, the verb, and a relationship. E.g., verifier, verify and verifying.

### Acronyms

The following terms are proper nouns or acronyms:
- ToIP
- W3C
- DIF
- X.509
- Diffie-Hellman
- KEL

### Special characters
Notice that the Acrynom `X.509` has a special character (`.`). You SHOULD use special characters only if it's crucial for the meaning of the term. 

So, for example, *not this*: `security@hub4issuer` but stick to the guidelines above and define, for example, `security-at-hub-for-issuer`.


### Constants, variables, and terms in coding
Sometimes, acronyms in code are (partly) in lowercase (e.g., `vLEI`, `eID`, `ind`) for various reasons. One needs to explain those acronyms in terms of concepts and terminology; we allow them to do so in their original case.

### Authors partly comply and have freedom of choice

#### Comply with
- all of the above-mentioned style guides
- the governance of terms using the current terminology source management tools

See the [Roles](roles) section for the various sub roles of an author.

## Terminology
[[def: proper noun]]
~ | TBW |