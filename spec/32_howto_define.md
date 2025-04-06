## How to write definitions in your terminology

1. Repeat the objectives or goals (of a specific group/community)
2. Discuss and communicate towards consensus about a particular concept or term
3. Define the scope or mental model together
4. Write criteria for which is inside or outside the reach of a specific term

This process is essential for mutual understanding.

### How to write criteria

1. Criteria must make sense for all roles involved in the community

> For example, a criterium like "A self-addressing identifier is automatically a self-sovereign identifier, but not the other way around." might not resonate with a Reader.

2. Criteria should be deterministic, either to be in or out of the definition

Example: **Acronym**
> [[def: self-certifying-identifier, SCID]]
> ~ a shorthand in capitals for a [[ref: {acronym}]]. It may contain special characters. It may not contain spaces.
> Criterium for not being an Acronym: If the word is not in uppercase, in our context, the word is more likely to be an [[ref: {alias}]] for the term.

3. Formulate edge cases: What is just included in a definition and excluded from a definition?!

> E.g., X.509 could be an acronym, and 'EU ID' is not an acronym

::: note Basic Note
A writer needs to do a lot of adding-criteria work before we discuss anything, like reusing definitions in another mental model. It just makes no sense to refer/link to a non-deterministic definition of somebody else, for this inherently introduces confusion: we think we are talking about the same thing, but most probably, we're not!
:::

#### As we go, we can do
An editor can achieve enhancement in the written version of concepts and terminology in parallel with other activities:
- archiving old concepts and glossaries
- tool development
- consensus building
Beware: **don't reference poorly-formulated definitions**, because that'll put a burden on the future.

### Towards automatic processing in github actions

Currently, we allow for two types of source management tools of terminologies. 
Check them out here: | TBW Link to the chapter |. 

Steps: 
1. Source management (`def`, `ref`, `xref` and `tref`)
2. Sticking to standardization rules
3. Processing automatically (using NPM and Github Actions)

Examples of standardizations:
1. introduce lowercase names with dashes between the words, example: `self-certifying-identifier`
2. don't **delete** items (i.e., .md files), but make clear they are depreciated and/or link to the new concept/term
3. don't change or **update** the name of an item single-handedly, for it might change the concept/meaning for other people and create dead links for those who **read** - or link to the term. Please open an issue or a PR to discuss first. 
4. any other immediate updates and amendments are welcome; the revisions are available for us to (partially) revert if something unwanted or unexpected happens.
5. Standardization of the use of acronyms. An acronym that is well-known and should be explained/linked to the term it abbreviates. Example: SCID, TSP. An acronym that is less/hardly known and links *only implicitly* to the term it abbreviates. Example: legitimized-human-meaningful-identifier, aka LID.
The use of "Also known as" is in both situations optional.

### Glossary processing

Whereas the source management tool (or *input tool*) alters the content of terminology and it's storage location, there should also be a way to add metadata (descriptive information).

Based on metadata it becomes possible to generate end-products that offers listing, search-functions, selection and filtering options.

Next step consists of:
- put terminology in online glossaries, Term-definition sections of specifications and in dictionaries.
- print terminology in hard-copy specifications (pdf and paper)

Some ToIP groups use workarounds to add metadata and extra functionality to their terminology based on the combination of labeling content and additional metadata

> E.g., the WebofTrust-harboured engine KERISSE regularly scrapes the the WOT-terms wiki into [KERISSE](http://kerisse.org), we add features and metadata through a Google Sheet, we connect relevant matching terms from related glossaries. Finally, we index it for the KERI Suite Search Engine (KERISSE).

### Spec-Up-T

Spec-Up-T is a static-page site generator. It's unique feature is it generates an all-encompassing sole internet page; one `index.html`.

The processing consists of:
- Updating NPM
- Updating specific NPM Spec-Up-T tools
- Run the Spec-Up-T menu by hand for additional functions
  - Generate the external references anew
  - Generate the single page website
- Investigate and lookup the results on a local computer
- Commit the changes on a local computer
- Push the result to a public internet server
- Generate the results using Github Actions on a public internet server