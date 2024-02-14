
[//]: # (Pandoc Formatting Macros)

[//]: # (\mainmatter)

[//]: # (\doctitle)

## Scope

This Guide goes with the flow as much as it can. This means:
- git and github for version control, issue-handling and project management in the own github repo
- The existing Slack group CTWG for discussions
- Use of github wiki-based source management of terminologies
- Proposal to archive obsolete sources of terminology
- Reuse harvesting / consensus creation tools that are available and anticipate improvements of those
- Connect to TEv2 step by step
- Use Spec-Up / specification template and anticipate improvements of this

### Roadmap

Let's clear up the issues around TEv2 versus Spec-Up and KERISSE tooling. The goal is unification and we prevent reinventing tools that are already in place.

The issue of unification is open, and it might be solved. By whom is not yet clear. A sequence numbered roadmap to unification (presumming that that's the goal) can be found below.


##### Temporary solution: pictures

![past](https://github.com/henkvancann/terminology-governance-guide/blob/fab622598a0bc03d0fedb62ea989572e082ae6bb/images/Gantt%20Diagram%20temporary%20past.png)

![future](https://github.com/henkvancann/terminology-governance-guide/blob/fab622598a0bc03d0fedb62ea989572e082ae6bb/images/Gantt%20Diagram%20temporary%20future.png)

```mermaid
gantt
    title Roadmap to Unification of Specification and Terminology
    dateFormat  YYYY-MM
    section 1. Spec-Up def/ref consistency
    A. Write Normative Spec           :a1, 2024-02, 30d
    B. Spec-Up improvements     :after a1  , 60d
    section 2. Specification Template
    A. Write Terminology Governance Guide      :2024-01  , 120d
    B. Contribute back SpecUp code: 2024-04, 100d
    section 3. Source management Terminologies
    A. Google Doc ToIP content : 2023-09, 200d
    B. ToIP central Glossary      : 20d
    C. Publish permanent links ToIP gloss : 24d
    section 4. Specification Template Task Force
    A. Decision tooling: 2024-02  21d
    B. Fork instead of Copy Template:24d
    section 5. KERISSE engine
    A. Search Engine glossary :2023-09, 60d
    B. Unified glossary :2023-11 , 50d
    C. Kerific browser extension: 40d
    D. Write Spec kerific consensus: 50d
    E. Consensus tool kerific: 2024-02-15, 120d
    section 6. TEv2 integration
    A. Study TEv2      :2024-02  , 90d
    B. Study Semantic Treehouse (STH): 2024-02-15, 30d
    C. Visit TNO results: 14d
    D. Testcase Group creation Glossary TEv2 : 30d
    E. Follow TEv2 integration in STH : 2024-04-1, 160d
```
