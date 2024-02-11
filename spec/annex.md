
[//]: # (Pandoc Formatting Macros)

[//]: # (# This is an annex {#sec:annexA .normative})

[//]: # (With some text)

[//]: # (# This is another annex {#sec:annexB .informative})

[//]: # (With some more text)

## Annex

### Comparison Spec-Up 2023 and TEv2 by Rieks Joosten, Jan 2024
This specification has used the following insights to write the Guidelines, most notably in the Roles section and the Normative section.

#### Spec-Up

I have had a look at the latest spec-up draft, specifically that relating to terminology. The text tells you about features it has, but (as often) you need to see the source of that text (in RAW format) to figure out how to do things if you're new to this. Here's my understanding:
Spec-up term definition syntax is as follows:

[[def: <term> ]]
~ <text that is used as the description/definition of 'term'>

where
<term> is the term that is being defined. The documentation doesn't say what it can(not) be, e.g., whether or not it may contain spaces or special characters, and

<text that is used...> appears to be a (single) line of text, which also isn't further specified.

If you want to specify aliases (what TEv2 calls 'form phrases'), you say:

[[def: <term>, <alias1>, <alias2> ... ]]
~ <text that is used as the description/definition of 'term' (and its aliases)>

where <term>and <text that is used...>  are as before, and <alias<i>> are the aliases, which are also not further specified, but the example shows they can contain spaces (so the , and the closing ]] are the delimiters for the term list.

#### TEv2 definitions appear in different forms:

As a set of a (curated) text files (markdown), one for each term. They contain (YAML) frontmatter in which there are fields for (a) the term, (b) the aliases (called 'form phrases') and (c) the text line (called 'glossaryTexts'). In their body, they contain more documentation related to the term.
as an entry in a machine-readable glossary (YAML). Every entry basically consists of not only the frontmatter of the curated text file, but also some other fields that (third party) tools can use to find the curated text file, or a rendered version thereof.
as a set of Wiki files, that will (soon?) be ingestable (turned into curated text files).

Spec-up use of term references within markdown:
[[ref: <term-or-alias>]]

where <term-or-alias> is the defined term or one of its aliases.
TEv2 use of termrefs can be done in different forms:
[<showtext>](@)

where <showtext> is a defined term or form phrase. However, if <showtext> is not a defined term or form phrase, you can still make it refer to a defined term using the syntax:
[<showtext>](term@)

TEv2 has additional syntax for using terms that refer to stuff
other than concepts (such as mental models, e.g., [<showtext>](pattern:jurisdiction@)
in other scopes, e.g., [parties](@essif-lab), in particular versions of a terminology, e.g., [tag](@tev2:latest)

Also, TEv2 has mechanisms where users can define/configure their own syntax for termrefs, and also mechanisms for specifying what a termref (when found) should be converted into.
Spec-up glossaries are a rendered version of the list of spec-up definitions, which requires them to all be specified in that same one location. When a user clicks on a termref (in the rendered version), it is taken to the location where the term is defined. I haven't seen any documentation of whether/how that would work with multiple files.
TEv2 glossaries come in two forms: machine readable glossaries (MRGs) and human readable glossaries (HRGs). TEv2 sees a HRG as a rendered reference to a particular MRG, so (like TermRefs) users can specify a so-called 'MRG-Ref' in their markdown, and when that is processed, a HRG is generated at that location from the designated MRG, in a format, and using contents that the user specifies. Here is an example of various HRGs generated in a single page.

#### Discussion

Spec-up is quite different from TEv2. Most notably, By design, spec-up is (very) simple to use, and has the basic features you need when writing (simple) specifications. When things become more complex, or you want to explicitly position a spec in a context where other specs also live, my guess is that you run into its limitations. But then, that's not what spec-up was designed to do.
TEv2 on the other hand is not simple when viewed from a single-context-perspective. But you can use and build on terminologies of others. Another source of perceived complexity may be caused by its flexibility, e.g., it allows users to specify syntaxes (for TermRefs and MRGRefs), as well as the (html, markdown or other constructs) that the can be converted into.

So the basic question seems to be whether or not there is an actual need for spec-up and/or TEv2 within ToIP, which I think we can ponder about by understanding what either can, or cannot do. 

[tno-terminology-design.github.io](tno-terminology-design.github.io)

Glossary Generation Demo | TNO Terminology Design

This page is evidence that an HRG can be generated for every MRG that is available within the scope. It also shows that HRGs can be generated in different formats.

Regarding the roles (specification author, curator, end-user/reader), some thoughts:

Authors come in different flavors. An author that writes specs has different capabilities (e.g., be precise and so) than an author that writes learning stuff (things for Muggles and so). Darrell can do git and markdown, but I recall that Nicky (and others) thought that to be too cumbersome. The minimalistic use-cases would differ for the different author sub-roles, so we should give some thought which sub-roles exist within ToIP.

When we were talking about the 'term communities', we also had the role of 'contributor', which is the role a person performs as (s)he helps draft criteria (for definitions), mental models and other stuff that we envisaged could be needed in a particular WG, TF (scope). Do we still think that way?

Apart from having the minimalistic use-cases, I think it would be helpful if, for every activity or product from the CTWG, we know
who would *actually* be using it, and
what they would need to be able to do with that
so that we can make sure that they can use it and do with it what they need to. And IMHO that is far from trivial, we we should give that some attention.