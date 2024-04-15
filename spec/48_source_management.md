

## Source Management Use Cases

Input knowledge level: You know how to create, read and update term definitions in relation to | TBW how to edit a wiki entry |

### What
This section is about the source management of term and definitions: the latest single source of truth about them in a certain scope. The elementary part is {term}.md file that contains (spec-up extended) markdown. We offer various ways of managing these source files with integrity.

### What can I do with it?
Source management culminates in the *latest version* of any glossary in which the term are accessible (linkable) with a *persistent URL* and we have a *history avaiable* who referered this term at what time in the past.
You can reference this glossary in your own write ups and add to the general consensus about terms at the same time.

### Why
We want to offer multiple ways to edit term definitions. So not wiki **or** markdown **or** github frontend but wiki **and** markdown **and** github frontend. 
The end-result is always a git(hub) tracked directory with separate .md files of a spec-up based specification. The use case are described below. The term definitions themselves use the spec-up markdown extensions syntax: `def`, `ref` and `xref`.

Example given:

``` markdown
[[def: access control]]: 
~ The process of granting or denying specific [[ref: request]]s for obtaining 
and using information and related information [[xref: processing]] services.
```

### Why not simply a Content Management System like Wordpress??!

1. user management in github ecosystem instead of centralized technological island creation
2. Spec-up static website generation, we don't want introduction of databases
3. Continuous Developement Continuous Integration (CDCI) versus staging by hand
4. Business rules and Permanent linking made possible via Github Actions
Just to name a few reasons.

### Who
The roles involved in the use cases are editor, production repo master and curator.
One person could have more than one role.

All roles have a github user account, because we need to know 
- *who* proposes a change on *what* and *when* this occurred.
- who changes what and when. 
Git keeps track.

He/she who has write user rights on the target repo (TrustoverIP main glossary)  can directly edit and commit the latest version. Other roles will have to adapt to those results. For example merge confilcts might arise and need to be solved.

Further guidelines:
- editors COULD have a fork of the repo. They NEED TO have a forked target repo for option 2, 3 and 4 below.
- curators don't need to have a user github repo, only a github user account and they use the functionality to comment on PRs.

### How 
Github Actions will pick up and process changes as they occur.

This is the process diagram

![Terms-dir-circular](https://github.com/trustoverip/ctwg-terminology-governance-guide/blob/eb572181e2e66fa8453162affa25b86a7c984838/images/Terms-dir-circular.png?raw=true)



These are the two main options we have use cases for:

- A. Wiki based = edits WITHOUT curation and PR are possible, see 1. below

- B. PR based WITH optinal curation and **mandatory** PRs, see option 2, 3 and 4 below.

### 1. Wiki

The terms-definitions directory will be exported to a clone of the target repo wiki by the production repo `master`. 
The wiki (sub) repo of a github repo allows for different user right settings than the repo itself.

GitHub allows the master to configure access permissions for wikis independently of the main repository settings. Here's how the permission settings can differ:

By default, a repository's wiki inherits the permissions from the repository itself. This means that if someone has write access to your repository, they can also edit the wiki. However, GitHub provides an option to modify these permissions specifically for the wiki. Under the "Settings" tab for the repository, the master will find a section for the wiki where he/she can choose to either:

a. Inherit permissions from the repository, meaning those with write access to the repository can edit the wiki.
b. Allow everyone with a GitHub account to edit the wiki, which makes the wiki more open, regardless of their access to the repository itself.

This flexibility allows project maintainers to either keep their wikis as collaborative spaces open to the wider GitHub community or restrict them to be consistent with the access controls applied to the source code in the repository. It's worth noting that these settings can be changed at any time by the repository owner or users with admin access to the repository.

Now `editors` can us the wiki of the target repo to CRU term definition. We describe separate use cases for C, R, U. Delete is very rare, because the history of terms should be kept available.

`Curators` could add markdown comments to the sources of the wiki.

> NB: Editing of the target github wiki repo on your local machine is possible but a rather strange way to manage sources of your terms definitions. But it can be done if you have the user rights: push the wiki repo to the target wiki repo.
> We advise to choose one of the other source management options, because it's more direct.

::: note Basic Note
After this source editing has been saved our solution also overwrites the repo file `/spec/splitted-dir/{term}.md` (if present) for syncing purposes.
:::

### 2. Github edit
Editors go the the term definition they want to C R U on the github.com user site of the target repo (which is controlled by master). 

This way editors can edit (after having forked the target repo to their own user account) the term definition and offer a PR to master. After the PR is made the curator can comment on the changes proposed and live viewable on the user account of the editor.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### 3. Terminal - text file edit

This way editors can edit (after having cloned the target repo to their own user account). He/she uses a text editor to write changes in the separate .md file of the term and definitions directory. He/she use git on the command line to add, commit and push files to their own github user account version of the target repo. From the target repo he/she creates a PR by hand for the curator and the master to assess and eventually accept or decline. After the PR is made the curator can comment on the changes proposed and live viewable on the user account of the editor.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### 4. IDE
An integrated Development Environment, e.g. Visual studio Code - text file edit

This way editors can edit (after having cloned the target repo to their own user account). He/she uses an IDE to write changes in the separate .md file of the term and definitions directory. He/she uses the IDE git functinality to finally create a PR on the target repo for the curator and the master to assess and eventually accept or decline. After the PR is made the curator can comment on the changes proposed and live viewable on the user account of the editor.

The input is a per-term splitted directory of term md files 
The end result is a 4 options to make changes and 2 options to get the results accepted in the target repo and final spec-up html output: Via 1. Wiki and via 2,3,4 : PR.

All methods have full git tracing of who did what and when.

::: note Basic Note
After this source editing have been saved our solution also overwrites the wiki repo file `/{term}.md` (if present) for syncing purposes.
:::

### How

The rest of this chapter outlines the use cases for managing term definitions in a spec-up based specification, focusing on the roles of editors, production repo masters, and curators.

We focus on **terms and definitions only**. We use the term *target repo* for the production repo, controlled by the role `master`.

### Roles

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
- Directly view the term's page in the Wiki section.

#### 2. GitHub Edit (via GitHub UI)

##### Create and Update (C/U)
- **Actor**: Editor
- **Process**:
  1. Fork the target repository to your GitHub account.
  2. In your fork, navigate to the `terms-definitions` directory.
  3. To add a new term, click "Add file" > "Create new file". To update, click on an existing `.md` file and then the pencil icon (Edit this file).
  4. Make changes or add the new term using markdown syntax. Commit the changes to a new branch in your fork, and start a pull request.

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
  1. For deleting a term, remove the `.md` file or edit its content to reflect the term's deprecation, committing with a clear rationale. Only in exceptional cases, because it's far better to archive instead of delete. So also the | LINK guidelines to edit text |
  2. Push the changes to the main branch and update any documentation accordingly.

#### Curator Review
- **Process**: Engage in PR discussions, offering feedback and suggestions to ensure clarity and correctness of term definitions.

#### Notes

- Merge conflicts may arise during the PR process, requiring coordination for resolution.
- All changes, including deletions, should be documented with clear commit messages and PR descriptions to maintain a transparent history of modifications.
