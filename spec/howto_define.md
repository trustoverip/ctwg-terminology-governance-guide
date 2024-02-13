## How to write definitions in your terminology

1. Repeat the objectives or goals of a certain community
2. Discuss, communicate towards consensus about a certain concept or term
3. Define the scope or mental model together
4. Write criteria for which is inside or outside the reach of a certain term

Needless to say, this process is important for mutual understanding.

### How to write criteria

1. Criteria must make sense for all roles involved in the community

> For example a criterium like "A self-adressing identifier is automatically a self-sovereign identifier, but not the other way around." might not resonate with a Reader.

2. Criteria should be deterministic, either to be in or out the definition

> [[def: abbrev, abbreviation]]
> ~ a shorthand in capitals for a [[ref: term]]. It may contain special characters. It may not contain spaces.  
> Criterium for not being an abbreviation: If the word is not in uppercase, in our context the word is more likely to be an [[ref: alias]] for the term.

3. Formulate edge cases: What is just included a defnition, and what is just excluded from a definition?!

> E.g. X.509 could be an abbreviation, and 'EU ID' is not an abbreviation

::: note Basic Note
A lot of adding-criteria work needs to be done, before we discuss anything like reusing definitions in another mental model. It just makes no sense to refer / link to a non-deterministic definition of somebody else, for this inherently introduces confusion: we think we are talking about the same thing, but most probably we're not!
:::

Some good news is that enhancement in the written version of concepts and terminology can be achieved in parallel with other activities:
- archiving old concept and glossaries
- tool development
- consensus building
But unfortunately **not together with referencing existing poorly-formulated definitions** because that'll put a burden on the future.

### Towards automatic processing in github actions


Currently github wikis serve as the source management tool of the glossary terms in ToIP context. There are temporary exceptions.

Here are a few [practical rules](https://wiki.trustoverip.org/display/HOME/Terms+Wikis) from the originator ToIP to get these wiki terms through their equivalent [github actions script](https://github.com/WebOfTrust/WOT-terms/actions/workflows/content-fetch-and-deploy-update-glossary.yml), please:
1. beware all new wiki items you **create**, lead to new .md files. We'd like to know
2. introduce lowercase names with spaces (they will convert into lower case names with dashes between the words)
3. start with **## Definition** header; [example](https://github.com/WebOfTrust/WOT-terms/wiki/composable-event-streaming-representation)
4. start with uppercase abbreviations with only the "**## See**" header; [example](https://github.com/WebOfTrust/WOT-terms/wiki/CESR)
5. don't **delete** items (i.e. .md files) but make clear they are depreciated and / or link to the new concept / term
6. don't change or **update** the name of an item single handed, for it might change the concept / meaning for other people and create dead links for those who **read** - or link to the term. Please open an issue or a PR to discuss first. 
7. any other immediate updates and amendments welcome, the revisions are available for us to be able to (partially) revert if something unwanted or unexpected happens.

_Have fun CRU-ing!_  
'* CRU=Create Read Update

### A glossary "reads" this wiki

Where as the wiki source management tool (or *input tool*) of terminology, there is no way to add metadata to the terminology.

Currently some ToIP groups use workarounds to add metadata and extra functionality to their wiki terminology, based on the combination of labelling content and extra metadata.
E.g. The WebofTrust-harboured engine KERISSE regularly scrapes the the WOT-terms wiki into [KERISSE](http://kerisse.org), we add features and metadata through a Google Sheet, we connect relevant matching terms from related glossaries and finally we index it for the KERI Suite Search Engine (KERISSE).

| TBW | 