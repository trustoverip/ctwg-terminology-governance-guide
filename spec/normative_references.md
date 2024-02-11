## Normative references
This section is normative.

The normative section we call the “Spec-Up glossary tool” (SGT); to give a name to the coding project for now.


#### Background
To simplify the job of tech spec construction and editing, the Technology Stack WG has adopted the Spec-Up spec editing tool which is originally a DIF open source project. Spec-Up has been used by TSWG spec authros including Darrell O'Donnell (ToIP Trust Registry Protocol Specification), Drummond Reed (ToIP Technology Architecture Specification), Lance Byrd (did:webs Method Specification) and Henk van Cann (WebofTrust kerific-spec and this Guide). All of them need basic glossary management in these specs. In the ToIP Technology Architecture Specification it's a long-desired feature to add an integrated glossary.

Spec-Up already has a basic glossary feature: def tags for defining glossary entries and ref tags for marking up terms in the spec that refer to def-tagged terms. As an author there are mainly just two additional features we would need in Spec-Up to have “MVP” glossary management for all the specs coming out of TSWG over the next few months.

#### Feature requests

**The first feature** is to add Spec-Up code that detects dangling refs and defs. In other words, code that checks to see that: a) any ref tag defined in the spec has a corresponding def tag for the glossary entry, and b) every def tag defining a glossary entry has at least one ref tag pointing to it.

**The second feature** addresses a current limitation of Spec-Up: ref tags can only reference def tags in the same Spec-Up document. Darrell had the brilliant idea that the CTWG should begin publishing the ToIP Glossary as its own standalone Spec-Up specification, where every entry is properly formatted with a Spec-Up def tag. If we do that, then all we need for any TSWG specification to be able to include terms from the ToIP Glossary (without having to copy those 400+ terms over into its own glossary) is to enhance Spec-Up code to support remote refs.



It should check each `def` created in a local Spec-Up document against *any `def`* that exists in any of the remote `ref` document URLs listed in the local document (see the “doctag” list description)

When a certain Spec-Up document includes a certain glossary from another Spec-Up document, this is a statement: "we think we might be on the same page as the people that maintain this glossary".
It's important to realize why somebody in which [role](./role.md#user-reader)

| TBW doctag |

### Internal definition (def)
definitions (`def`s)

```
[[def: term { | abbrev}, {alias}, {alias}, ... ]]
~ Lorem Ipsum ...
```
{optinal}

A `term` SHOULD be defined as a ToIP definition style : lower case

An `alias` COULD be referenced. If you do so the reference MUST end up at the definition of `term` This is already operational in the current version of Spec-Up and implemented with nested spans

::: ISSUE
https://github.com/henkvancann/terminology-governance-guide/issues/1
:::

> Check `defs` of aliases https://github.com/decentralized-identity/spec-up/blob/master/single-file-test/spec.md#term-references
and the working `refs` here https://identity.foundation/spec-up/#term-references


`abbrev` COULD be defined and referenced. If you do so a seperate definition of `abbrev` MUST be present in the document itself:

```
[[def: abbrev]]
~ [the term the abbrev refers to]

Example of the duplet:

[[def: KEL]]
~ [[ref: key event log]]

[[def: key event log | KEL, Key-event log ]]
~ Lorem Ipsum ...

```

#### Don't do this
```
[[def: term (abbrev)]] and  
[[ref: phrase]]
```
but do this
```
[[def: term | abbrev]]
```
How to add an abbreviation after the term? Two ways possible:
1. in the markdown, but NOT in the reference to the term:
  [[ref:]]
There will be post-markdown processing available to proportionally add abbreviation

### Internal linking (ref)

```
[[ref: phrase]]
```
`phrase` MUST be one of `term`, `abbrev` or `alias`


Three ways of offering references (`ref`s) to definitions (`def`s) by the author of a text:
1. explicitly created by author
2. extra by default, after n occurrences or below a header of certain level


1. MUST be done in the source by hand
2. MUST be done by code, we'll add a data-attribute to the resulting hrml that indicates the origin of the link.

### External linking (ref)

We need the capability for all ToIP specs to use remote refs to reference a common ToIP Glossary in addition to their own internal glossary. So far an inventarisation under TSWG spec authors would be fine with that capability: they can use any term already defined in the ToIP Glossary without having to repeat it in their glossary, and they can add any term specific to their spec.
 

```
[[ref: group#phrase]]
```
`phrase` MUST be one of `term` in any of `group`'s glossary.

For example, a specification that includes a ref tag that looks like this: [[ref:toip#term]] would reference a def tag defined in the ToIP Glossary. Similarly, a ref that looks like [[ref:hxwg#term]] would reference a defined term in the (theoretical) HXWG glossary.

With this remote reference feature, all ToIP specifications (and any other deliverable written with Spec-Up) would be able to include linked glossary terms (including hover pop-up definitions) both from within its own glossary and from any referenced glossary in another document that also uses Spec-Up.

Mind you, this process touches group dynamics, consensus building and communication.

| TBW dangers of bluntly referencing and copying |


Technically, the only difference between a local ref and a remote ref is that the former are always within the same Spec-Up document — they look like:

[[ref:term]]

The latter allow the author to reference a def in a different Spec-Up document. They look something like:

[[ref:doctag#term]] or [[ref-glossary1:term]]

[[ref: doctag]] is a short unique tag assigned to the remote Spec-Up document containing the def for the term being referenced. So any Spec-Up document that uses remote refs would need to include a doctag section that looks something like this:

[[doctags:

[toip:https://trustoverip.github.org/cwtg/toip-glossary.md]

[hxwg:https://trustoverip.github.org/hxwg/hxwg-glossary.md]

]]

| TBW where is the registry to ensure uniqueness of doctags and prevention of duplicious doctags? |


Judith Fleenor asked for Rieks Joosten viewpoint on this proposal for using Spec-Up refs and defs. He explained that the same features being discussed here were also added to TEv2. There is always tension between adding a lot of features and taking a long time, or keeping things very minimal. He pointed out that creating glossaries based on cherry-picking glossary entries based on personal preferences can be problematic because it doesn't actually establish shared understanding and criteria for defining terms. The larger the group involved, and the more varied their cultural backgrounds, the more problematic that can become. However, that doesn't mean we shouldn't start with tools that are actually working right now. Riek's personal preference is to use terminology that expresses the author's intentions clearly. For example, in reading the Spec-Up documentation, it was challenging for Rieks to understand it without more context.

Rieks Joosten would like to have several more sessions on TEv2 so we can still look at how we can use it for our terminology.

Judith Fleenor summarized Riek's feedback as saying that he's not opposed to enhancing Spec-Up for these features, but at the same time keeping TEv2 tooling in progress. 

Darrell O'Donnell clarified that he and Kevin will not delete any ToIP repos, but will only archive them.

Rieks Joosten concluded that we need to see what tools are actually needed by both authors and readers to help them comprehend the terms they use. He can also explore how TEv2 tooling can be used to produce Spec-Up definitions.

Judith Fleenor asked if we had a clear decision about Brian Richter to make the proposed changes to Spec-Up.

Drummond Reed asked if there were any objections.

Kevin Griffin was in favor of moving forward at the use of both types of tools (Spec-Up and TEv2) and will provide his input per his action item above.

Rieks Joosten was in favor of proceeding with these changes to Spec-Up, but also to continue the work on TEv2 to tackle larger issues of terminology management. He also pointed out this Confluence tool: https://marketplace.atlassian.com/apps/1219677/smart-terms-for-confluence-glossary?tab=overview&hosting=cloud 

DECISION: We will proceed to ask Brian Richter to make the proposed code contributions to Spec-Up to add the dangling ref/def and remote ref features as described in the 2024-01-29 CTWG meeting notes.





## System feature Consistency

Consistency and rules for [[def:]]s and [[ref:]]s leads to github.io page with all kinds of working internal and external links and clear rules for writers.

### Basic domain checks
1. characterset
2. spaces
   | TBW |
   
### Domain checks Spe-Up or github actions
1. No abbrevs in the text of a term either in "()" or after ";"
2. The system must warn for double aliases in one def
3. The system must warn for double abbrevs in one def
4. No duplicity in wording in term, abbrev and alias(ses)
5. If term and abbrev are the same, discard abbrev
6. If alias and term are the same, discard alias
7. If abbrev and alias are the same, discard alias


| TBW What is 'the same' ? |

### Parser checks Spe-Up or github actions
1. The system must warn for double aliases in more than one def
2. The system must warn for double abbrevs in more than one def
3. The system must report broken internal links, refs that don't match term, abbrev nor aliasses.

### External Consistency
We like reuse of existing terminology, laid out in definitions and glossaries. If applied correctly, reuse will increase consensus within TrustoverIP.

Given this positive effect we encourage people to look what's there already before defining and writing your own definition.

How do we know which known glossary to use? Maybe any glossary we have previously created a cross reference from should be included?
There is already tooling available to include existing glossaries and give a unified overview of them in [KERISSE](https://weboftrust.github.io/WOT-terms/docs/glossary-unified?level=2). This listing can be adjusted to "ToIP only".



### No effective system without governance

The governance rules that we have to put in place (at least with the ToIP community) should be:

1. If the spec authors want to use a term with its definition term as defined in the ToIP Glossary, the spec authors MUST insert a remote ref to that term in their spec and MUST NOT copy the term (or worse, redefine it) in their internal spec glossary.

2. If the spec authors want to use a term defined in the ToIP Glossary but modify its definition, they COULD submit raise an issue and/or a pull request to the ToIP Glossary making the case for their proposed change. If that change is resolved to their satsifaction, they can proceed as per rule #1 above.

3. If the spec authors want to use a new term that does not exist in the ToIP Glossary to their liking, they have two choices:
- If the spec authors believe the term should apply “ToIP community-wide”, they can submit a PR to have it added to the ToIP Glossary. If accepted, they can then follow rule #1 above.
- If the spec authors believe the term only applies in the scope of their particular spec, they can define it with a def tag in their own internal spec glossary and then ref it there.

Of course, this set of rules only works within an coherent community willing to follow them. We can’t control the use of terminology outside of the ToIP community.



## System feature functionality

The front-end functionality of the resulting github.io page can and must be altered to comply with various Reader allowances:
- Only so and so often a link to known term in the glossary
- Only so and so often an abbreviation of term added to the term in the core text
- Pop-ups consistenly showing definitions while hovering over the term
- Consensus tooling (kerific) as a browser extension

| TBW |


## System feature layout
The front-end layout and pdf layout of the resulting github.io page can and must be altered to comply with various style-guide rules of external parties like IETF or ISO.


| TBW |

[//]: # (Pandoc Formatting Macros)

[//]: # (# Normative references)

[//]: # (::: { #nrm:pdf2 .normref label="ISO 32000-2" })

[//]: # (ISO 32000-2, *Document management --- Portable Document Format --- Part 2: PDF 2.0*)

[//]: # (:::)
