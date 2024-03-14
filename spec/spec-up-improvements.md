## Normative addendum - Spec-up improvements

This normative section is also called the “Spec-Up glossary tool” (SGT).

#### Background
To simplify the job of tech spec construction and editing, the Technology Stack WG has adopted the Spec-Up document rendering tool which is originally a DIF open source project ([repo](https://github.com/decentralized-identity/spec-up)). 

#### Objective

Based on use cases of certain roles we'd like to technically specify improvements in a normative way, so that they can be implemented right away and connected to issues.

In each topical section (header level 3) there'll be various sub-topics (header level 4)
- features
- consistenty checks
- domain checks
- business rules

### refs

One def and 1 to many refs may be present in a spec-up source document.

#### features

For an author there are mainly three relevant functionalities.
1.  Spec-Up already has a basic glossary feature: `def` tags for defining glossary entries and `ref` tags for marking up terms in the spec that refer to def-tagged terms. Def tags only reference def tags *in the same* Spec-Up document.


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



##### System feature Consistency

Consistency and rules for [[def:]]s and [[ref:]]s leads to github.io page with all kinds of working internal and external links and clear rules for writers.

   
#### Consistency pre-caution

Each `ref` has an existing `def`. Each `def` has at least one `ref` or `xref`. 

Spec-Up code that detects dangling `refs` and `defs`. In other words, code that checks to see that: 
   a. any ref tag defined in the spec has a corresponding def tag for the glossary entry, and  
   b. every def tag defining a glossary entry has at least one ref tag pointing to it.


#### Domain checks
- `term`, or (optional) `alias` or (optional) `abbreviation` of the term definition used to reference

**Local references**

The most important domain check between a local ref and def is that they're always pointing back and forth in the same Spec-Up document — they look like:
`[[def: term, alias, ..., alias ]]`

`[[ref: phrase]]` where phrase is one of `term` or optional `alias`es.


**Basic domain checks**

1. characterset
2. spaces
   [[def:<term>]] and [[def: <term>]]
3. Uppercase versus lowercase
4. Form Phrases
   | TBW |
   
**Domain checks Spe-Up or github actions**

1. No abbrevs in the text of a term either in "()" or after ";"
2. The system must warn for double aliases in one def
3. The system must warn for double abbrevs in one def
4. No duplicity in wording in term, abbrev and alias(ses)
5. If term and abbrev are the same, discard abbrev
6. If alias and term are the same, discard alias
7. If abbrev and alias are the same, discard alias

| TBW What is 'the same' ? |

#### Business rules

::: note Usecase Author
If the spec authors believe the term only applies in the scope of their particular spec, they can define it with a def tag in their own internal spec glossary and then ref it there.
:::

**Parser checks Spe-Up or github actions**

1. The system must warn for double aliases in more than one def
2. The system must warn for double abbrevs in more than one def
3. The system must report broken internal links, refs that don't match term, abbrev nor aliasses.

### xrefs

We need the capability for all ToIP specs to use  `xref`s to reference a common ToIP Glossary in addition to their own internal glossary. The common glossary will be referenced with `title`.

::: note Usecase Author
TSWG spec authors would like to use any term already defined in the ToIP Glossary without having to repeat it in their glossary, and they can add any term specific to their spec.
:::


2. An `xref` tag to enhance Spec-Up code to support *remote* refs.
  
#### Features

##### Feature Title and title collections

It is possible to include references to terms from external spec-up generated specifications. To include a source you would like to pull references from include an external_specs array in your spec config. The value should be a key/value object where the key is used in the external reference below and the value is the URL of the external spec.

To include an external term reference within your spec use the following format `[[xref: {title}, {term}]]` where `{title}` is the title given to the spec in the `specs.json` configuration file and `{term}` is the term being used. 

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


##### How to adopt a term "as is"? {#adopt-asis}

*Local* preferable
`[[ref: term]]` 

Or *remote* reference

`[[xref: title, term]]` 

Where `term` is either a term, abbreviation or alias.

#### Consistency pre-caution

Each `xref` has an existing `def` in the `title` glossary.

Spec-Up code that detects dangling `refs` and `defs` in the collection of `title`s. In other words, code that checks to see that: 
   a. any ref tag defined in a spec has a corresponding def tag for the glossary entry somewhere in the collection of `titles`, and  
   b. every def tag defining a glossary entry in any of the `title`s including the local one. has at least one ref tag in any of the `title`s pointing to it.

#### Domain checks

see [refs](#refs) for applicable initial domain constraints; plus the following.

**Remote references**

`[[xref: title, term]]` is a short unique tag assigned to the remote Spec-Up document containing the def for the term being referenced. So any Spec-Up document that uses remote refs would need to include a doctag section that looks something like this:

In specs.json:
```
      "external_specs": [
        {
          "<title>": "<URL>"
        }
```
example
```
      "external_specs": [
        {
          "PE": "https://identity.foundation/presentation-exchange"
        }
```

#### Business rules

::: note Rule 1 Author
If the spec authors want to use a term with its definition term as defined in the ToIP Glossary, the spec authors MUST insert a remote ref to that term in their spec and MUST NOT copy the term (or worse, redefine it) in their internal spec glossary.
:::

::: note Rule 2 Author
If the spec authors want to use a term defined in the ToIP Glossary but modify its definition, they COULD submit raise an issue and/or a pull request to the ToIP Glossary making the case for their proposed change. If that change is resolved to their satsifaction, they can proceed as per rule #1 above.
:::

::: note Rule 3 Author
If the spec authors want to use a new term that does not exist in the ToIP Glossary to their liking, and they believe the term should apply “ToIP community-wide”, they can submit a PR to have it added to the ToIP Glossary. If accepted, they can then follow rule #1 above.
:::

::: warning People involved!
Of course, this set of rules only works within an coherent community willing to follow them. We can’t control the use of terminology outside of the ToIP community.
:::

It should **check** each `ref` and `xref` created in reference `title` against *any `def`* that you're about to **remove** from a local file. 

It should **signal** each `ref` and `xref` created in reference `title` against *any `def`* that you're about to **change** in a local file. 


### Add context to adoption of a term

Adopting a term from a related scope (under the ToIP umbrella) or external SHOULD always be accompagnied with a possibility for the author, curator and maybe even other team members to add context to the definition adopted. 

#### Features context and metadata
The following metadata MUST be registered:
- `term`, or (optional) `alias` or (optional) `abbreviation` of the term definition used to reference
- `url` of the spec in which the term definition list is present and the name of the header
- `commit hash` of the term definition plus specification adopted
- `authenticated github user` that adopts the term (create), changes it's context (update) or deletes the context.

This metadata SHOULD be added:

- `title` of the group from which the term will be adopted
- `role` of the `authenticated github user` in the current scope

You COULD add or remove:
- `context` which is a block of free text.

##### How to adopt a term with added or updated context? {#adopt-context}

Add:
`[[def: term or abbreviation or alias]]` with in the text part of the definition

`[[xref: title, term]]` 

Reference:

`[[ref: term]]` 

**Example**
Where `KE` is the title of KERI spec in spec-up format and `TP` the title of the ToIP overall glossary in spec-up.

```

[[def: verification]]

~ Verification in Healthcare is in between the strict [[xref: KE, verification]]
 and the more loose ToIP definition [[xref: TP, verification]]. However we have the same criteria as KERI
  because our system will be KERI-based.

```

#### Consistency pre-caution

| TBW |

#### Business rules

The **order in which these changes take place** to a terminology definition, referencing and/or commenting SHOULD be registered.

Mind you: the adopter of a term SHOULD NOT delete, nor alter the original definition, present in another scope.

##### How to stop adding context to an adopted term?

Remove the local `def` and change

`[[ref: term]]` into `[[xref: term]]`

Now the term is again externally referenced "as is".

### Authentication and roles

It's important to make explicit that somebody in a certain [role](./role.md#user-reader) added context to a remotely referenced term definition. Or he/she has chosen to refrain from that.


```
[[ref: title#phrase]]
```
`phrase` MUST be one of `term` in any of `title`'s glossary.

For example, a specification that includes a `ref` tag that looks like this: `[[xref : toip, term]]` would reference a def tag defined in the ToIP Glossary. Similarly, a ref that looks like `[[ref: hxwg, term]]` would reference a defined term in the (theoretical) HXWG glossary.

With the remote reference feature, all ToIP specifications (and any other deliverable written with Spec-Up) would be able to include linked glossary terms (including hover pop-up definitions), both from within its own glossary and from any referenced glossary in another document that also uses Spec-Up.

::: warning Non-technical characteristic
Mind you, this process touches group dynamics, consensus building and communication.
:::

### External Consistency
We like reuse of existing terminology, laid out in definitions and glossaries. If applied correctly, reuse will increase consensus within TrustoverIP.

Given this positive effect we encourage people to look what's there already before defining and writing your own definition.

::: note KERISSE
How do we know which known glossary to use? Maybe any glossary we have previously created a cross reference from should be included?
There is already tooling available to include existing glossaries and give a unified overview of them in [KERISSE](https://weboftrust.github.io/WOT-terms/docs/glossary-unified?level=2). This listing can be adjusted to "ToIP only".
:::


### System feature functionality

The front-end functionality of the resulting github.io page can and must be altered to comply with various Reader allowances:
- Only so and so often a link to known term in the glossary
- Only so and so often an abbreviation of term added to the term in the core text
- Pop-ups consistenly showing definitions while hovering over the term
- Consensus tooling (kerific) as a browser extension

| TBW |


### System feature layout
The front-end layout and pdf layout of the resulting github.io page can and must be altered to comply with various style-guide rules of external parties like IETF or ISO.


| TBW |

[//]: # (Pandoc Formatting Macros)

[//]: # (# Normative references)

[//]: # (::: { #nrm:pdf2 .normref label="ISO 32000-2" })

[//]: # (ISO 32000-2, *Document management --- Portable Document Format --- Part 2: PDF 2.0*)

[//]: # (:::)
