## User manual defs, refs and xrefs

#### Background
To simplify the job of tech spec construction and editing, the Technology Stack WG has adopted the Spec-Up spec editing tool, which was originally a DIF open-source project ([here](https://github.com/decentralized-identity/spec-up)). 

TrustoverIP invests in improving this tool. It's currently at Blockchainbird's [Spec-Up-T](https://github.com/blockchainbird/spec-up-t) repository only but will eventually move to [ToIP](https://github.com/trustoverip/spec-up-t).

This document also contains a [normative section](#spec-up-improvements) that has served as a design for the coding project since the start of 2024.

#### Objective
To offer authors and curators a hands-up guide to handle Spec-up's syntax correctly and efficiently with regard to `defs`, `refs` and `xrefs`. Thereby respecting the golden rule:

 "Try `(x)ref` before `def`"

([why?](#try-ref-before-def))

#### Characteristics
Why bother? Because it's going to be a mess soon if you don't. Terminology has a life cycle. Some concepts and their specific terminology are long-lived. They reside in their field and are related to other concepts. Other terminologies are contemporary. Terminology can have broad applications or, conversely, have a specific small niche. Nevertheless, they all share these characteristics:
1. The sources (definitions or defs) need to be managed because its content is burdened with reputation
2. References (or refs and xrefs) need to be managed in the digital world where creating copies is easy, and every copy for no reason whatsoever might cause confusion
3. Different roles and responsibilities work with and work on terminology. We got to keep track of who did what in which role. 

#### Governance of own repo
The governance of def & refs in the own repo has to be strict: It has to be kept sound by humans. So check your refs to see if you changed the def.  
[Source](https://wiki.trustoverip.org/display/HOME/2024-07-01+CTWG+Meeting+Notes)

#### ToIP glossary

 In the ToIP Technology Architecture Specification, it's a long-desired feature to add an integrated glossary. Our objective is to offer a framework to offer this in a sustainably consistent way. The Concept & Terminology work group (CTWG) should begin publishing the ToIP Glossary as its own standalone Spec-Up specification, where every entry is properly formatted, and people are able to include terms from the ToIP Glossary (without having to copy those 400+ terms over into its own glossary).

**Process check:**

You should visually check each `def` created in a local Spec-Up document against *any `def`* that exists in any of the remotely referenced document URLs listed in the local document (see the `title` list description in your `specs.json`).

To find the list, look for `external_specs:`

```
 "external_specs": [
 {
 "TP": "https://trustoverip.github.io/ctwg-main-glossary/"
 }
 ...
```

##### Why "try ref before def" {#try-ref-before-def}

These are the advantages of trying ref before def:
- consensus building: if you study defs of related scopes under the same umbrella, you'll become more knowledgeable and aware of the different fields
- less work: it's easier to adopt a definition with well-formed criteria than having to [design one](#terminology-design-aids) yourself
- leading by example: your refs might be copied, enforcing the reputation of the def at hand.
  
Keep reading for an **important caveat** to these advantages! (No, [bring me there](#caveat-copy-def) now)  

**Decide whether you'd like to adopt as is, adopt with a comment, or define yourself.** See [flow diagram](#flow-of-writing-a-specification-in-spec-up)

#### Functionality
For an author, there are three main relevant functionalities.
1. Spec-Up already has a basic glossary feature: `def` tags for defining glossary entries and `ref` tags for marking up terms in the spec that refer to def-tagged terms. Def tags only reference def tags *in the same* Spec-Up document.
2. An `xref` supports *remote* refs.

::: note Status
March 2024 - The feature "xref" is constructed but not yet operational
:::

3. We have functionality that detects dangling `refs` and `defs`. In other words, code that checks to see that: 
 a. any ref tag defined in the spec has a corresponding def tag for the glossary entry, and  
 b. every def tag defining a glossary entry has at least one ref tag pointing to it.

Supported consistency pre-cautions and reporting:

::: note Status
March 2024 - The feature "checks" is being constructed step-by-step but not yet fully operational.
:::

Each `def` in a local Spec-Up document has **exactly the same** `def`* existing in any of the remotely referenced document URLs listed in the local document (see the `title` list description in your `specs.json`). This is also a recommended visual check performed by authors. ([Why?]({#try-ref-before-def}))

Each `ref` has an existing `def`. Each `xref` has an existing `def` in the `title` glossary.

It **checks** each `ref` and `xref` created in reference `doctags` against *any `def`* that you're about to **remove** from a local file. 

It **signals** each `ref` and `xref` created in reference `doctags` against *any `def`* that you're about to **change** in a local file.  

When a local Spec-Up document includes a certain glossary from another remote Spec-Up document, this can be considered as a statement: "We think we might be on the same page as the people that maintain this glossary."

It's important to make explicit that somebody in a certain [role](./role.md#user-reader) added context to a remotely referenced term definition. Or he/she has chosen to refrain from that.

#### Title (formerly "Doctag")

##### External linking (ref)

We need the capability for all ToIP specs to use remote refs to reference a common ToIP Glossary in addition to their own internal glossary. So far, an incentivization under TSWG spec authors would be fine with that capability: they can use any term already defined in the ToIP Glossary without having to repeat it in their glossary, and they can add any term specific to their spec.

```
[[ref: group#phrase]]
```
`phrase` MUST be one of `term` in any of `group`'s glossary.

For example, a specification that includes a `ref` tag that looks like this: [[ref:toip#term]] would reference a def tag defined in the ToIP Glossary. Similarly, a ref that looks like [[ref:hxwg#term]] would reference a defined term in the (theoretical) HXWG glossary.

With this remote reference feature, all ToIP specifications (and any other deliverable written with Spec-Up) would be able to include linked glossary terms (including hover pop-up definitions), both from within its own glossary and from any referenced glossary in another document that also uses Spec-Up.

Mind you, this process touches on group dynamics, consensus building, and communication.

##### Dangers of bluntly referencing and copying  {#caveat-copy-def}

It's important to note that team members in various [roles](#Roles) should feel free to define a term as they wish, **after studying what's available**. This is an important caveat for referencing terms.

#### Add context and metadata

::: note Status
March 2024 - The feature "context metadata" is in the design phase, so it is not operational
:::

Adopting a term from a related scope (under the ToIP umbrella) or externally has the possibility for the author, curator, and maybe even other team members to add context to the definition adopted. The following metadata will be (automatically as much as possible) registered:

- `term`, or (optional) `alias` or (optional) `abbreviation` of the term definition used to reference
- `URL` of the spec in which the term definition list is present and the name of the header
- `commit hash` of the term definition plus specification adopted
- `authenticated GitHub user` that adopts the term (create), changes its context (update) or deletes the context.

This metadata can be added:

- `group name` from which the term will be adopted
- `role` of the `authenticated GitHub user` in the current scope

You could add or remove:
- `context`, which is a block of free text.

The **order in which these changes take place** to a terminology definition, referencing, and/or comments will be registered.

Mind you: the adopter of a term can't delete nor alter the original definition present in another scope.

#### Local versus Remote references
Technically, the only difference between a local ref and a remote ref is that the former are always within the same Spec-Up document — they look like:

`[[ref: term]]`

The latter allows the author to reference a def in a different Spec-Up document. They look something like:

::: note Status
March 2024 - The feature "xref" is under testing, so it is not fully operational yet
:::

`[[xref: title, term]]` is a short unique tag assigned to the remote Spec-Up document containing the def for the term being referenced. So, any Spec-Up document that uses remote refs would need to include a `doctag` section that looks something like this:

In `specs.json`:
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
 },
 {
 "TP": "https://trustoverip.github.io/ctwg-main-glossary/"
 }
 ...
```

### Adopt, add context, or define

::: note Status
March 2024 - The feature "context metadata" is in the design phase, so it is not operational
:::

Check the flow diagram of writing terminology (references) in a specification [here](#flow-of-writing-a-specification-in-spec-up).

##### How do we adopt the term "as is"? {#adopt-asis}

*Local* preferable
`[[xref: term]]` 

Or *remote* reference

`[[xref: title, term]]` 

Where `term` is either a term, abbreviation, or alias.

##### How do you adopt a term with added or updated context? {#adopt-context}

::: note Status
March 2024 - The feature "adopt a term with context and metadata" is in the design phase, so it is not operational
:::

Add:
`[[def: term or abbreviation or alias]]` with in the text part of the definition

`[[xref: title, term]]` 

Reference:

`[[ref: term]]` 

**Example**
Where `KE` is the `title` (doctag) of the KERI spec in spec-up format and `TP` is the title of the ToIP overall glossary in spec-up.

```

[[def: verification]]

~ Verification in Healthcare is in between the strict [[xref: KE, verification]]
 and the more loose ToIP definition [[xref: TP, verification]]. However, we have the same criteria as KERI
 because our system will be KERI-based.

```

##### How do you stop adding context to an adopted term?

::: note Status
March 2024 - The feature "adopt a term with context and metadata" is in the design phase, so it is not operational.
:::

Remove the local `def` and change.

`[[ref: term]]` into `[[xref: term]]`

Now, the term is again externally referenced as "as is."

### Form phrase macros
By: Rieks Joosten, July 1 2014

How to deal with singular/plural forms, here's my 2 cents:
TL;DR: In order to support different forms of terms, I suggest to follow the ideas from TEv2:
Allow a definition syntax that supports what TEv2 calls **form phrase macros**. For example, `[[def: actor{ss} ]]`, or `[[def: part{yies}]]`
Consider making the mapping between form phrase macros and the strings they represent configurable. For example, `{ss}` maps to the set of strings: "", "s", "'s", "s'".
When converting a document, make a list of the definitions, and replace every term therein with the string that results from resolving the form phrase macros therein (if any) and regularizing the results. This would result in [[def: actor, actors, actor's, actors']]. Regularization is a mechanism that facilitates the machine's handling of texts, similar to how titles of Wiki pages are converted into the corresponding parts of their URLs. Regularization would turn `[[def: Term 1, Term One]]` into `[[def: term-1, term-one]]`.
When converting a REF or XREF, use the regularized version of the term used in the (X)REF to look for the definition.

#### Elaboration Form phrase macros
Here is some elaboration/background:
I think the issue is broader: it's not just singular/plural forms (of nouns), e.g., "actor", "actors", "party", "parties", but also their possessive forms "actor's", "actors'", "party's", "parties". It's also various conjugation forms of verbs, e.g., "define", "defines", "defined", "defining", or "identify", "identifies", "identified", and "identifying".
To come to grips with this broader issue, TEv2 introduces "form phrases", i.e., one of the (multiple) forms in which concepts can be referred to. For example, the form phrases "actor", "actors", "actor's", etc. all refer to the same concept. That's why they can be specified in (the formPhrases field of) the curated text that documents that concept.
To reduce the work for creating such form phrases (and indeed, also to prevent typing mistakes!), TEv2 also introduces "form phrase macros", i.e., little strings, such as "{ss}" or "{yies}" that can be included in a form phrase, and represent a particular kind of variations. For example, "actor{ss}" is shorthand for "actor", "actors", "actor's" and "actors'". Similarly, "part{yies}" is short for "party," "party's," and "parties." A number of such form phrase macros are predefined, but you can override this set of macros with a set of your own, which is useful if texts are written in other languages (French, Dutch) or if you want or need to do your own. When generating the machine-readable glossaries (MRGs, the authoritative sources of terminologies/definitions as far as TEv2 is concerned), all form phrases as specified in the curated texts are converted into a canonical form (a regularized text), and their macros are expanded. Thus, an MRG entry only contains regularized form phrases, which helps with easy processing.
TEv2 includes a TermRef Resolution Tool (TRRT) that converts termrefs into so-called 'renderable refs'.

TermRefs are identified by a regex (called the TRRT interpreter) that is expected to populate particular variables, one of which is called show text, which contains the text that will be rendered. Another is called `term`; it contains the default name for the concept being referenced. The TRRT finds all texts that satisfy the regex and will replace them in the end with a character sequence that we call a 'renderable ref' (see point c)
The variables (named capturing groups) are then used to find the MRG that contains the term being referenced (there is a default MRG in case such variables are empty). From the selected or default MRG, a single entry needs to be found that corresponds with the termref. This is done by using the term variable (which often is empty) or, when it is empty, by using the showtext variable (which always exists) as a starting point. These texts are first processed into some canonical form, called a regularized text, so that they can be used to compare with entries in the formPhrases field of MRG entries. When a match is found, that MRG entry will be selected to create the renderable ref.

A 'renderable ref' is created by executing a handlebars template, which can access all fields in the MRG entry, as well as all named capturing groups as populated by the regex. This means that it is fully up to those who run the tool to determine what the renderable ref looks like.
The TEv2 MVP has an interpreter for Spec-Up term references, meaning it can find constructs of the form` [[ref: {showtext}]]` and `[[ref: {showtext}, {term}]]` as valid references.  It can also find constructs of the form `[[xref: {scopetag}, {showtext}]]`. All that is needed is a proper regex that finds occurrences of such syntax and populates the appropriate named capturing groups. The modification to also support syntaxes such as `[[xref: {scopetag}:{vsntag}, {showtext}]]` are trivial.

[Source Rieks Joosten July 1 2024](https://trustoverip.slack.com/archives/C01BBNGRPUH/p1719842141807949)

### Normative section

Have a look at it [here](#spec-up-improvements) and be informed that Spec-Up is a longer running open source project that [originated in DIF](https://github.com/decentralized-identity/spec-up). ToIP will invest in improvements to it in 2024. And offers these improvements as PRs to the DIF repo.

Here, we focus on the informative aspects of the technical specification: what it is, why we are programming it, and how to use it.

It is possible to include references to terms from external spec-up generated specifications. To include a source you would like to pull references from, include an external_specs array in your spec config. The value should be a key/value object where the key is used in the external reference below, and the value should be the URL of the external spec.

To include an external term reference within your spec, use the following format `[[xref: {title}, {term}]]` where `{title}` is the title given to the spec in the `specs.json` configuration file and `{term}` is the term being used. 

For example, using the `PE` spec given in this example:
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

#### Internal definition (def)
definitions (`def`s)

::: note Status
The feature "abbreviation" is under construction!
:::

```
[[def: term { | abbrev}, {alias}, {alias}, ... ]]
~ Lorem Ipsum 
```
{optinal}

Define a `term` in a ToIP definition style: lowercase.

Optionally, an `alias` could be referenced. If you do so, the reference MUST end with the definition of `term`. Test by simply clicking the link.

::: note More Info
Check `defs` of aliases https://github.com/decentralized-identity/spec-up/blob/master/single-file-test/spec.md#term-references
and the working `refs` here: https://identity.foundation/spec-up/#term-references
:::

An `abbrev` could be defined and referenced. If you do so, a separate definition of `abbrev` must be present in the document itself.

::: note Status
March 2024 - This feature "abbrev" is in the design phase, so not operational
:::

##### Don't do this
```
[[def: term (abbrev)]] and  
[[ref: phrase]]
```
But do this

::: note Status
March 2024 - This feature "abbrev" is in the design phase, so not operational
:::

```
[[def: term | abbrev]]
```
How do you add an abbreviation after the term? Two ways possible:
1. in the markdown, but NOT in the reference to the term:
 [[ref:]]
2. There will be post-markdown processing available to proportionally add the abbreviation


#### Internal linking (ref)

```
[[ref: phrase]]
```
`phrase` MUST be one of `term`, `abbrev` or `alias`.

Three ways of offering references (`ref`s) to definitions (`def`s) by the author of a text:
1. explicitly created by the author
2. extra by default, after n occurrences or below a header of a certain level

1. MUST be done in the source by hand
2. MUST be done by code; we'll add a data attribute to the resulting HTML that indicates the origin of the link.

| TBW, where is the registry to ensure the uniqueness of doctags and the prevention of duplicitous doctags? |


## System feature Consistency

Have a look at it [here](#spec-up-improvements) and be informed that Spec-Up is a longer running open source project that [originated in DIF](https://github.com/decentralized-identity/spec-up). ToIP will invest in improvements to it in 2024. And offers these improvements as PRs to the DIF repo.

The tool will perform
- Basic domain checks
- Domain checks Spe-Up or GitHub actions
- Parser checks Spe-Up or GitHub actions

### External Consistency
We like the reuse of existing terminology laid out in definitions and glossaries. If applied correctly, reuse will increase consensus within TrustoverIP.

Given this positive effect, we encourage people to look at what's there already before defining and writing their own definition.

How do we know which known glossary to use? Maybe any glossary we have previously created a cross-reference from should be included?
There is already tooling available to include existing glossaries and give a unified overview of them in [KERISSE](https://weboftrust.github.io/WOT-terms/docs/glossary-unified?level=2). This listing can be adjusted to "ToIP only".


### No effective system without governance

The governance rules that we have to put in place (at least with the ToIP community) should be:

1. If the spec authors want to use a term with its definition term as defined in the ToIP Glossary, the spec authors MUST insert a remote ref to that term in their spec and MUST NOT copy the term (or worse, redefine it) in their internal spec glossary.

2. If the spec authors want to use a term defined in the ToIP Glossary but modify its definition, they COULD raise an issue and/or a pull request to the ToIP Glossary, making the case for their proposed change. If that change is resolved to their satisfaction, they can proceed as per rule #1 above.

3. If the spec authors want to use a new term that does not exist in the ToIP Glossary to their liking, they have two choices:
- If the spec authors believe the term should apply “ToIP community-wide”, they can submit a PR to have it added to the ToIP Glossary. If accepted, they can then follow rule #1 above.
- If the spec authors believe the term only applies in the scope of their particular spec, they can define it with a def tag in their own internal spec glossary and then ref it there.

Of course, this set of rules only works within a coherent community willing to follow them. We can’t control the use of terminology outside of the ToIP community.

## System feature functionality  {#post-processing}

The front-end functionality of the resulting github.io page can and must be altered to comply with various Reader allowances:
- Only so and so often is a link to a known term in the glossary
- Only so and so often is an abbreviation of a term added to the term in the core text
- Pop-ups consistently showing definitions while hovering over the term
- Consensus tooling (kerific) as a browser extension

| TBW |


## System feature layout
The front-end layout and pdf layout of the resulting GitHub.io page can and must be altered to comply with various style-guide rules of external parties like IETF or ISO.

| TBW |

