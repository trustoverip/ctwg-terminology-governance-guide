## How to write definitions in your terminology

1. Repeat the objectives or goals of a specific community
2. Discuss and communicate towards consensus about a particular concept or term
3. Define the scope or mental model together
4. Write criteria for which is inside or outside the reach of a specific term

This process is essential for mutual understanding.

### How to write criteria

1. Criteria must make sense for all roles involved in the community

> For example, a criterium like "A self-addressing identifier is automatically a self-sovereign identifier, but not the other way around." might not resonate with a Reader.

2. Criteria should be deterministic, either to be in or out of the definition

> [[def: abbrev, abbreviation]]
> ~ a shorthand in capitals for a [[ref: term]]. It may contain special characters. It may not contain spaces.  
> Criterium for not being an abbreviation: If the word is not in uppercase, in our context, the word is more likely to be an [[ref: alias]] for the term.

3. Formulate edge cases: What is just included in a definition and excluded from a definition?!

> E.g., X.509 could be an abbreviation, and 'EU ID' is not an abbreviation

::: note Basic Note
A writer needs to do a lot of adding-criteria work before we discuss anything, like reusing definitions in another mental model. It just makes no sense to refer / link to a non-deterministic definition of somebody else, for this inherently introduces confusion: we think we are talking about the same thing, but most probably, we're not!
:::

Some good news is that an editor can achieve enhancement in the written version of concepts and terminology in parallel with other activities:
- archiving old concepts and glossaries
- tool development
- consensus building
Unfortunately, **not together with referencing existing poorly-formulated definitions** because that'll put a burden on the future.

### Towards automatic processing in github actions

Currently, we allow for four types of source management tools of terminologies in the ToIP context. 
Check them out here: | TBW Link to the chapter |.

This example uses the github.com wiki of the target repository, but the other source management options could adopt the same guidelines for designing and editing terminology in the ToIP context. 

Here are a few [practical rules](https://wiki.trustoverip.org/display/HOME/Terms+Wikis) from the originator ToIP to get these wiki terms through their equivalent [github actions script](https://github.com/WebOfTrust/WOT-terms/actions/workflows/content-fetch-and-deploy-update-glossary.yml), please:
1. beware all new wiki items you **create**, lead to new .md files. Because we'd like to know about new definitions, flaunt them in discussions or social media: throw links!
2. introduce lowercase names with spaces (they will convert into lowercase names with dashes between the words)
3. start with **## Definition** header; [example](https://github.com/WebOfTrust/WOT-terms/wiki/composable-event-streaming-representation)
4. start with uppercase abbreviations with only the "**## See**" header; [example](https://github.com/WebOfTrust/WOT-terms/wiki/CESR)
5. don't **delete** items (i.e., .md files), but make clear they are depreciated and/or link to the new concept/term
6. don't change or **update** the name of an item single-handedly, for it might change the concept/meaning for other people and create dead links for those who **read** - or link to the term. Please open an issue or a PR to discuss first. 
7. any other immediate updates and amendments are welcome; the revisions are available for us to (partially) revert if something unwanted or unexpected happens.

_Have fun CRU-ing!_  
'* CRU=Create Read Update

### A glossary "reads" this 

| TBW, this section is draft and incomplete|

Whereas the wiki source management tool (or *input tool*) of terminology, there is no way to add metadata to the terminology.

Some ToIP groups use workarounds to add metadata and extra functionality to their wiki terminology based on the combination of labeling content and additional metadata.
E.g., the WebofTrust-harboured engine KERISSE regularly scrapes the the WOT-terms wiki into [KERISSE](http://kerisse.org), we add features and metadata through a Google Sheet, we connect relevant matching terms from related glossaries. Finally, we index it for the KERI Suite Search Engine (KERISSE).

| TBW | 