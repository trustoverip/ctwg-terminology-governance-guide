## User manual defs and refs

The normative section we call the “Spec-Up glossary tool” (SGT); to give a name to the coding project for now.

#### Background
To simplify the job of tech spec construction and editing, the Technology Stack WG has adopted the Spec-Up spec editing tool which is originally a DIF open source project. 

#### Objective (informative)
Terminology has a life cycle. Some concepts and its specific terminology are long lived. They reside in their field related to other concepts. Other terminologies are contemporary. Terminology can have broad application or conversely have a very specific small niche. Nevetheless, they all share these characteristics:
1. The sources need to be managed because its content is burdened with reputation
2. References need to be managed in the digital world where creating copies is easy
3. Different roles and responsibilities work on a terminology. We got to keep track who did what in which role. 
 
 In the ToIP Technology Architecture Specification it's a long-desired feature to add an integrated glossary. Our objective is to offer a framework to offer this in a sustainably consistent way. The Concept & Terminology work group (CTWG) should begin publishing the ToIP Glossary as its own standalone Spec-Up specification, where every entry is properly formatted and people are able to include terms from the ToIP Glossary (without having to copy those 400+ terms over into its own glossary).

Process check:

You should visually check each `def` created in a local Spec-Up document against *any `def`* that exists in any of the remotely referenced document URLs listed in the local document (see the “doctag” list description).

**Decide whether you'd like to adopt as is, adopt with comment or define yourself.** See [flow diagram](#flow-of-writing-a-specification-in-spec-up)

#### Objective (normative)
For an author there are mainly three relevant functionalities.
1.  Spec-Up already has a basic glossary feature: `def` tags for defining glossary entries and `ref` tags for marking up terms in the spec that refer to def-tagged terms. Def tags only reference def tags *in the same* Spec-Up document.
2. An `xref` tag to enhance Spec-Up code to support *remote* refs.
3. Spec-Up code that detects dangling `refs` and `defs`. In other words, code that checks to see that: 
   a. any ref tag defined in the spec has a corresponding def tag for the glossary entry, and  
   b. every def tag defining a glossary entry has at least one ref tag pointing to it.

Consistency pre-caution:

Each `ref` has an existing `def`. Each `xref` has an existing `def` in the `doctag` glossary.

It should **check** each `ref` and `xref` created in reference `doctags` against *any `def`* that you're about to **remove** from a local file. 

It should **signal** each `ref` and `xref` created in reference `doctags` against *any `def`* that you're about to **change** in a local file.  

| TBW | 

When a local Spec-Up document includes a certain glossary from another remote Spec-Up document, this can be considered as a statement: "we think we might be on the same page as the people that maintain this glossary".

It's important to make explicit that somebody in a certain [role](./role.md#user-reader) added context to a remotely referenced term definition. Or he/she has chosen to refrain from that.

#### Doctag (informative)

##### External linking (ref)

We need the capability for all ToIP specs to use remote refs to reference a common ToIP Glossary in addition to their own internal glossary. So far an inventarisation under TSWG spec authors would be fine with that capability: they can use any term already defined in the ToIP Glossary without having to repeat it in their glossary, and they can add any term specific to their spec.

```
[[ref: group#phrase]]
```
`phrase` MUST be one of `term` in any of `group`'s glossary.

For example, a specification that includes a `ref` tag that looks like this: [[ref:toip#term]] would reference a def tag defined in the ToIP Glossary. Similarly, a ref that looks like [[ref:hxwg#term]] would reference a defined term in the (theoretical) HXWG glossary.

With this remote reference feature, all ToIP specifications (and any other deliverable written with Spec-Up) would be able to include linked glossary terms (including hover pop-up definitions), both from within its own glossary and from any referenced glossary in another document that also uses Spec-Up.

Mind you, this process touches group dynamics, consensus building and communication.

##### Dangers of bluntly referencing and copying

It's important to note that team members in various [roles](#Roles) should feel free to define a term as they wish, **after studying what's available**.

#### Add context and metadata
Adopting a term from a related scope (under the ToIP umbrella) or external SHOULD always be accompagnied with a possibility for the author, curator and maybe even other team members to add context to the definition adopted. The following metadata MUST be registered:

- `term`, or (optional) `alias` or (optional) `abbreviation` of the term definition used to reference
- `url` of the spec in which the term definition list is present and the name of the header
- `commit hash` of the term definition plus specification adopted
- `authenticated github user` that adopts the term (create), changes it's context (update) or deletes the context.

This metadata SHOULD be added:

- `group name` from which the term will be adopted
- `role` of the `authenticated github user` in the current scope

You COULD add or remove:
- `context` which is a block of free text.

The **order in which these changes take place** to a terminology definition, referencing and/or commenting SHOULD be registered.

Mind you: the adopter of a term SHOULD NOT delete, nor alter the original definition, present in another scope.

#### Local versus Remote references
Technically, the only difference between a local ref and a remote ref is that the former are always within the same Spec-Up document — they look like:

`[[ref: term]]`

The latter allow the author to reference a def in a different Spec-Up document. They look something like:

`[[xref: doctag, term]]` 

[[ref: doctag]] is a short unique tag assigned to the remote Spec-Up document containing the def for the term being referenced. So any Spec-Up document that uses remote refs would need to include a doctag section that looks something like this:

[[doctags:

[toip:https://trustoverip.github.org/cwtg/toip-glossary.md]

[hxwg:https://trustoverip.github.org/hxwg/hxwg-glossary.md]

]]

### Adopt, add context or define

Check the flow diagram of writing terminology (references) in a specification [here](#flow-of-writing-a-specification-in-spec-up).

##### How to adopt a term "as is"? {#adopt-asis}

*Local* preferable
`[[xref: term]]` 

Or *remote* reference

`[[xref: doctag, term]]` 

Where `term` is either a term, abbreviation or alias.

##### How to adopt a term with added or updated context? {#adopt-context}

Add:
`[[def: term or abbreviation or alias]]` with in the text part of the definition

`[[xref: doctag, term]]` 

Reference:

`[[ref: term]]` 

**Example**
Where `KE` is the doctag of KERI spec in spec-up format and `TP` the doctag of the ToIP overall glossary in spec-up.

```

[[def: verification]]

~ Verification in Healthcare is in between the strict [[xref: KE, verification]]
 and the more loose ToIP definition [[xref: TP, verification]]. However we have the same criteria as KERI
  because our system will be KERI-based.

```

##### How to stop adding context to an adopted term?

Remove the local `def` and change

`[[ref: term]]` into `[[xref: term]]`

Now the term is again externally referenced "as is".

#### Doctag (normative)

It is possible to include references to terms from external spec-up generated specifications. To include a source you would like to pull references from include an external_specs array in your spec config. The value should be a key/value object where the key is used in the external reference below and the value is the URL of the external spec.

To include an external term reference within your spec use the following format `[[xref: {doctag}, {term}]]` where `{doctag}` is the title given to the spec in the `specs.json` configuration file and `{term}` is the term being used. 

For example using the `PE` spec given in this example:
```json
{
  "specs": [
    {
      ...
      "external_specs": [
        {"PE": "https://identity.foundation/presentation-exchange"}
      ]
    }
  ]
}
```

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


| TBW where is the registry to ensure uniqueness of doctags and prevention of duplicious doctags? |


## System feature Consistency

Consistency and rules for [[def:]]s and [[ref:]]s leads to github.io page with all kinds of working internal and external links and clear rules for writers.

### Basic domain checks
1. characterset
2. spaces
   [[def:<term>]] and [[def: <term>]]
3. Uppercase versus lowercase
4. Form Phrases
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
