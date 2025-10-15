
## Source Management Use Cases

:::note Note
Input knowledge level: You know how to create, read, and update term definitions fit for your concept or mental model.
:::

### What is source management about?
This section is about the technical processing/source management of terms and definitions: the latest single source of truth about them in a certain scope. Spec-Up-T is the tool we discuss. The elementary part in Spec-Up-T is the `{term}.md` file that contains markdown and Spec-Up-T-specific tags. We offer various ways of managing these source files while maintaining their overall integrity.

### What can I do with it?
Source management culminates in the *latest version* of any glossary in which the term is accessible (linkable) with a *permanent URL*, and we have a *history available* that referred to this term at what time in the past.

:::info
You can reference to any Spec-Up-T-based glossary in your own write-ups and add to the general consensus about terms at the same time.
:::

### Why source management?
We want to offer multiple ways to edit term definitions. So it is not markdown **or** github frontend but markdown **and** github frontend.
The end result is always a git(hub) tracked directory with separate `.md` files of a Spec-up-T-based specification. The use cases are described below. The term definitions themselves use the Spec-Up-T markdown extensions syntax: `def`, `ref`, `tref` and `xref`.

Examples given:

``` markdown
[[def: access-control-list, access-control-list, ACL]]: 
~ The process of granting or denying specific [[ref: request]]s for obtaining 
and using information and related information [[xref: toip2, processing]] services.
```


``` markdown
[[tref: toip1, access-control, Access control]] 
```

### Why not simply use a Content Management System like WordPress??!

Just to name a few reasons:
1. User management and version control in the github ecosystem instead of centralized technological island creation
2. Spec-Up-T static website generation; we don't want the introduction of databases
3. Continuous Development Continuous Integration (CDCI) versus staging by hand
4. Business rules and Permanent linking made possible via Github Actions
5. Consensus-building within scopes but also between scopes
6. Mapping of locally defined terms, aliases and spelling.

### For who is source management of terminology relevant?
The roles involved in the use cases are `editor`, `production repo` master and `curator`.

One person could have more than one role.

**All roles above have a github user account**, because we need to know 
- *who* proposes a change on *what* and *when* this occurred.
- who changes what and when. 
Git keeps track of the changes we provoke.

:::info Info
Only the `Reader` role doesn't need a GitHub account.
:::

He/she who has `write` user rights on the target repo (e.g. TrustoverIP main glossary) can directly edit and commit the latest version. Other roles will have to adapt to those results.

 For example *merge conflicts* might arise and then need to be solved.

The good news is that Spec-Up-T has a mechanism for fallback to local versions of a definition if the original owner decides to update or delete it.
We'll get into more detail about fall-back options.

Further guidelines:
- Editors COULD have a fork for the repo. They NEED TO have a forked target repo for options 2, 3, and 4 below.
- curators don't need to have a user github repo, only a github user account, and they use the functionality to comment on PRs.

### How it works
Github Actions will pick up, and process changes as they occur and trigger staging of chancing to the production server.

This is the process diagram:

![Terms-dir-circular](https://github.com/trustoverip/ctwg-terminology-governance-guide/blob/eb572181e2e66fa8453162affa25b86a7c984838/images/Terms-dir-circular.png?raw=true)


There are two main options we have use cases for:
- Local computer
- On Github.com

All are PR based WITH optional curation and **mandatory** PRs; see options 1, 2, and 3 below.

### 1. Github edit
Editors go to the term definition they want to use for C R U on the github.com user site of the target repo (which is controlled by Master). 

This way, editors can edit (after having forked the target repo to their own user account) the term definition and offer a PR to Master. After the PR is made, the curator can comment on the changes proposed and make them live and viewable on the editor's user account.

::: note Basic Note
After this source editing has been saved, our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### 2. Terminal - text file edit

This way, editors can edit the target repo (after having cloned it to their own user account). He/she uses a text editor to write changes in the separate .md file of the term and definitions directory. He/she uses git on the command line to add, commit, and push files to their own github user account version of the target repo. From the target repo, he/she creates a PR by hand for the curator and the Master to assess and eventually accept or decline. After the PR is made, the curator can comment on the changes proposed and make them live and viewable on the editor's user account.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### 3. IDE
An integrated Development Environment, e.g., Visual Studio Code - text file edit.

This way, editors can edit the target repo (after having cloned it to their own user account). He/she uses an IDE to write changes in the separate .md file of the term and definitions directory. He/she uses the IDE git functionality to finally create a PR on the target repo for the curator and the Master to assess and eventually accept or decline. After the PR is made, the curator can comment on the changes proposed and make them live and viewable on the editor's user account.

#### Source management of terminology wrapped up

**The input** is a per-term-splitted directory of term md files
**The process**: four options to make changes 
**The end result** two options to get the results accepted in the target repo and final Spec-Up-T html output: Via 1. and via 2,3: all PR-based.

All methods have full git tracing of who did what and when.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### How it works in use cases

The rest of this chapter outlines the use cases for managing term definitions in a Spec-Up-T-based specification, focusing on the roles of editors, production repo masters, and curators.

We focus only on **terms and definitions**. We use the term *target repo* for the production repo, controlled by the role `master`.

### Roles in the use cases

- **Editor**: Individuals proposing changes to term definitions.
- **Production Repo Master (Master)**: Oversees the merging of PRs and has the authority to delete term definitions.
- **Curator**: Engages in reviewing proposed changes to enhance quality and accuracy.

### 4. Editing Options

#### 1. GitHub Edit (via GitHub UI)

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Fork the target repository to your GitHub account.
  2. In your fork, navigate to the `terms-definitions` directory.
  3. To add a new term, click "Add file" > "Create new file". To update, click on an existing `.md` file and then the pencil icon (Edit this file).
  4. Make changes or add the new term using markdown syntax. Commit the changes to a new branch in your fork and start a pull request on the target repo.

##### Read (R)
- View the `.md` files directly in the target repository or through the proposed changes in pull requests.

#### 2. Terminal - Text File Edit

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Clone your fork of the target repository to your local machine using the terminal: `git clone [Your-Fork-URL]`.
  2. Navigate to the `terms-definitions` directory within your local repository.
  3. Use a text editor to create a new `.md` file or update an existing one with the term definition.
  4. Use Git commands to add (`git add .`), commit (`git commit -m "your message"`), and push (`git push origin main`) the changes.
  5. Create a pull request from your GitHub fork's page.

#### 3. IDE - Visual Studio Code Text File Edit

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Clone your fork of the target repository into Visual Studio Code (VS Code) using its Git: Clone command.
  2. Navigate to the `terms-definitions` directory within the VS Code Explorer.
  3. Create a new `.md` file or edit an existing one, using markdown for the term definition.
  4. Commit the changes using the Source Control panel in VS Code, pushing them to your fork.
  5. Initiate a pull request via GitHub's website from your fork to the original repository.

### 5. Master and Curator Actions

#### Update (U) by Master
- **Process**: Review, potentially edit, and merge pull requests. Manage and resolve any merge conflicts.

#### Delete (D) by Master
- **Process**:
  1. For deleting a term, remove the `.md` file or edit its content to reflect the term's deprecation, committing with a clear rationale. Only in exceptional cases, because it's far better to archive instead of delete.
  2. Push the changes to the main branch and update any documentation accordingly.

#### Curator Review
- **Process**: Engage in PR discussions, offering feedback and suggestions to ensure clarity and correctness of term definitions.

#### Notes

- Merge conflicts may arise during the PR process, requiring coordination for resolution.
- All changes, including deletions, should be documented with clear commit messages and PR descriptions to maintain a transparent history of modifications.

### 6. Being a host for x- and t- referenced glossaries

The governance rules for Glossaries that apply to be a referenced glossary (like ToIP main Glossary, KERI, General Glossary) is best summarized in this one sentence:

**Your Index.html is leading on github.com.**

Any guest using `tref` or the `xref` tag to an external glossary will generate an API call, and get the index.html files over from their externally referenced glossaries and distill the right xref or tref information from those.

It's the responsibility of every host to:

- keep all `.md` files on github.com in sync with their live `Index.html` file of Spec-Up-T
- have successful runs of their *Github Action Scripts* that generate the `Index.html` file
- differentiate between the `main` branch (production) and other branches on github.com
- have `index.html` be at least as young as any of the .md files that contain term definitions on github.com on the `main` branch.
  
The reason for these source management rules is consistency: How can a guest be sure to have the latest term definition if the host would not have the latest version live in its own production glossary?  