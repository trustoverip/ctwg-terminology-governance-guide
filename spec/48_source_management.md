

## Source Management Use Cases

Input knowledge level: You know how to create, read, and update term definitions in relation to your concept or mental model. Here are some guidelines: [edit wiki term definitions](#towards-automatic-processing-in-github-actions)

### What is this about?
This section is about the source management of terms and definitions: the latest single source of truth about them in a certain scope. The elementary part is the `{term}.md` file that contains (spec-up extended) markdown. We offer various ways of managing these source files while maintaining their overall integrity.

### What can I do with it?
Source management culminates in the *latest version* of any glossary in which the term is accessible (linkable) with a *permanent URL*, and we have a *history available* that referred to this term at what time in the past.

:::info
You can reference this glossary in your own write-ups and add to the general consensus about terms at the same time.
:::

### Why source management?
We want to offer multiple ways to edit term definitions. So it is not wiki **or** markdown **or** github frontend but wiki **and** markdown **and** github frontend?
The end result is always a git(hub) tracked directory with separate `.md` files of a spec-up-based specification. The use cases are described below. The term definitions themselves use the spec-up markdown extensions syntax: `def`, `ref` and `xref`.

Example given:

``` markdown
[[def: access control]]: 
~ The process of granting or denying specific [[ref: request]]s for obtaining 
and using information and related information [[xref: processing]] services.
```

### Why not simply use a Content Management System like WordPress??!

Just to name a few reasons:
1. user management in the github ecosystem instead of centralized technological island creation
2. Spec-up static website generation; we don't want the introduction of databases
3. Continuous Development Continuous Integration (CDCI) versus staging by hand
4. Business rules and Permanent linking made possible via Github Actions

### For who is source management of terminology relevant?
The roles involved in the use cases are `editor`, `production repo` master and `curator`.
One person could have more than one role.

**All roles have a github user account**, because we need to know 
- *who* proposes a change on *what* and *when* this occurred.
- who changes what and when. 
Git keeps track of us.

He/she who has `write` user rights on the target repo (TrustoverIP main glossary) can directly edit and commit the latest version. Other roles will have to adapt to those results. For example *merge conflicts* might arise and then need to be solved.

Further guidelines:
- Editors COULD have a fork for the repo. They NEED TO have a forked target repo for options 2, 3, and 4 below.
- curators don't need to have a user github repo, only a github user account, and they use the functionality to comment on PRs.

### How it works
Github Actions will pick up, and process changes as they occur and trigger staging of chancing to the production server.

This is the process diagram:

![Terms-dir-circular](https://github.com/trustoverip/ctwg-terminology-governance-guide/blob/eb572181e2e66fa8453162affa25b86a7c984838/images/Terms-dir-circular.png?raw=true)


There are two main options we have use cases for:

- A. Wiki-based = edits WITHOUT curation and PR are possible; see 1. below

- B. PR based WITH optional curation and **mandatory** PRs; see options 2, 3, and 4 below.

### 1. Wiki

Go to the wiki of your project repo on github.com (which is controlled by Master). The wiki offers edit functionality.

> DEEP DIVE: This is what happens if you can straight away save the wiki pages you edit:
> The terms-definitions directory will be exported to a clone of the target repo wiki by the production repo `master`. 
> The wiki (sub) repo of a github repo allows for different user-right settings than the repo itself.

GitHub allows the Master to configure access permissions for wikis independently of the main repository settings. Here's how the permission settings can differ:

By default, a repository's wiki inherits the permissions from the repository itself. This means that if someone has write access to your repository, they can also edit the wiki. However, GitHub provides an option to modify these permissions specifically for the wiki. Under the "Settings" tab for the repository, the Master will find a section for the wiki where he/she can choose to either:

a. Inherit permissions from the repository, meaning those with write access to the repository can edit the wiki.
b. Allow everyone with a GitHub account to edit the wiki, which makes the wiki more open, regardless of their access to the repository itself.

This flexibility allows project maintainers to either keep their wikis as collaborative spaces open to the wider GitHub community or restrict them to be consistent with the access controls applied to the source code in the repository. It's worth noting that these settings can be changed at any time by the repository owner (Master) or users with admin access to the repository.

#### CRUD

Now, `editors` can use the wiki of the target repo to define the CRU term. We describe separate use cases for Create, Read, and Update (CRU). Delete (D) is very rare because the history of terms should be kept available.

`Curators` could add markdown comments to the sources of the wiki.

::: note Info Note
NB: Editing the target github wiki repo on your local machine is possible, but it is a rather strange way to manage sources of your terms definitions. But it can be done if you have the user rights: push the wiki repo to the target wiki repo.
We advise you to choose one of the other source management options because it's more direct.
:::

::: note Basic Note
After this source editing has been saved, our solution also overwrites the repo file `/spec/splitted-dir/{term}.md` (if present) for syncing purposes.
:::

### 2. Github edit
Editors go to the term definition they want to use for C R U on the github.com user site of the target repo (which is controlled by Master). 

This way, editors can edit (after having forked the target repo to their own user account) the term definition and offer a PR to Master. After the PR is made, the curator can comment on the changes proposed and make them live and viewable on the editor's user account.

::: note Basic Note
After this source editing has been saved, our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### 3. Terminal - text file edit

This way, editors can edit the target repo (after having cloned it to their own user account). He/she uses a text editor to write changes in the separate .md file of the term and definitions directory. He/she uses git on the command line to add, commit, and push files to their own github user account version of the target repo. From the target repo, he/she creates a PR by hand for the curator and the Master to assess and eventually accept or decline. After the PR is made, the curator can comment on the changes proposed and make them live and viewable on the editor's user account.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### 4. IDE
An integrated Development Environment, e.g., Visual Studio Code - text file edit.

This way, editors can edit the target repo (after having cloned it to their own user account). He/she uses an IDE to write changes in the separate .md file of the term and definitions directory. He/she uses the IDE git functionality to finally create a PR on the target repo for the curator and the Master to assess and eventually accept or decline. After the PR is made, the curator can comment on the changes proposed and make them live and viewable on the editor's user account.

#### Source management of terminology wrapped up

**The input** is a per-term-splitted directory of term md files
**The process**: four options to make changes 
**The end result** two options to get the results accepted in the target repo and final spec-up html output: Via 1. Wiki and via 2,3,4: PR.

All methods have full git tracing of who did what and when.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### How it works in use cases

The rest of this chapter outlines the use cases for managing term definitions in a spec-up-based specification, focusing on the roles of editors, production repo masters, and curators.

We focus only on **terms and definitions**. We use the term *target repo* for the production repo, controlled by the role `master`.

### Roles in the use cases

- **Editor**: Individuals proposing changes to term definitions.
- **Production Repo Master (Master)**: Oversees the merging of PRs and has the authority to delete term definitions.
- **Curator**: Engages in reviewing proposed changes to enhance quality and accuracy.

### Editing Options

#### 1. Wiki Editing

##### Create (C)
- **Actor**: Editor
- **Process**:
  1. Navigate to the GitHub repository page of the target repo.
  2. Access the Wiki section via the repository's main page menu.
  3. Click "New Page" to add a term, title the page with the term name, and detail the definition using markdown syntax.
  4. Click "Save Page" to finalize.

##### Update (U)
- **Process**: Similar to "Create", but select an existing term's page to edit.

##### Read (R)
- Directly view the term's page in the Wiki section. Mind you, this is an extra view & search option of the resulting glossary.

#### 2. GitHub Edit (via GitHub UI)

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Fork the target repository to your GitHub account.
  2. In your fork, navigate to the `terms-definitions` directory.
  3. To add a new term, click "Add file" > "Create new file". To update, click on an existing `.md` file and then the pencil icon (Edit this file).
  4. Make changes or add the new term using markdown syntax. Commit the changes to a new branch in your fork and start a pull request on the target repo.

##### Read (R)
- View the `.md` files directly in the target repository or through the proposed changes in pull requests.

#### 3. Terminal - Text File Edit

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Clone your fork of the target repository to your local machine using the terminal: `git clone [Your-Fork-URL]`.
  2. Navigate to the `terms-definitions` directory within your local repository.
  3. Use a text editor to create a new `.md` file or update an existing one with the term definition.
  4. Use Git commands to add (`git add .`), commit (`git commit -m "your message"`), and push (`git push origin main`) the changes.
  5. Create a pull request from your GitHub fork's page.

#### 4. IDE - Visual Studio Code Text File Edit

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Clone your fork of the target repository into Visual Studio Code (VS Code) using its Git: Clone command.
  2. Navigate to the `terms-definitions` directory within the VS Code Explorer.
  3. Create a new `.md` file or edit an existing one, using markdown for the term definition.
  4. Commit the changes using the Source Control panel in VS Code, pushing them to your fork.
  5. Initiate a pull request via GitHub's website from your fork to the original repository.

### Master and Curator Actions

#### Update (U) by Master
- **Process**: Review, potentially edit, and merge pull requests. Manage and resolve any merge conflicts.

#### Delete (D) by Master
- **Process**:
  1. For deleting a term, remove the `.md` file or edit its content to reflect the term's deprecation, committing with a clear rationale. Only in exceptional cases, because it's far better to archive instead of delete. So also [edit wiki term definitions](#towards-automatic-processing-in-github-actions).
  2. Push the changes to the main branch and update any documentation accordingly.

#### Curator Review
- **Process**: Engage in PR discussions, offering feedback and suggestions to ensure clarity and correctness of term definitions.

#### Notes

- Merge conflicts may arise during the PR process, requiring coordination for resolution.
- All changes, including deletions, should be documented with clear commit messages and PR descriptions to maintain a transparent history of modifications.
