## Integration
This is an informative section

Spec-Up, Spec-Up Glossary tool, TEv2 and the KERISSE-engine plus kerific tooling are gradually going to integrated for the sake of concept & terminology management in ToIP.

This section might why we anticipate with this Governance Guide on future development the way we've done in the previous sections.

### Concerns
We share some concern raised over the first months in 2024.

#### Spec-Up and Specification Template

Current copy and paste strategy leading to merge horror "unrelated histories".

```mermaid
flowchart TD
    DIF --> |SpecUp_Daniel_Buchner| SpecUp_60ae636
    SpecUp_60ae636 --> |PR accepted| SpecUp_d392aa1
    SpecUp_d392aa1 --> |commit| SpecUp_e63f252
    SpecUp_e63f252 --> |commit| SpecUp_985a65b
    SpecUp_60ae636 --> |copy Specification Template| ToIP_SpecUp_60ae636
    ToIP_SpecUp_60ae636 --> |PR accepted| SpecUp_445a7db
    SpecUp_445a7db --> |PR accepted| SpecUp_7667ec3
    SpecUp_7667ec3 -->  |copy | Spec_kerific
    SpecUp_7667ec3 --> |copy |keri-spec
    SpecUp_7667ec3 --> |copy | acdc-spec
    SpecUp_445a7db --> |copy | cesr-spec
    ToIP_SpecUp_60ae636 --> |copy| trp-spec
    ToIP_SpecUp_60ae636 --> |copy| tas-spec

    style DIF fill:#ffc;
    style SpecUp_60ae636 fill:#ffc;
    style SpecUp_d392aa1 fill:#ffc;
    style SpecUp_e63f252 fill:#ffc;
    style SpecUp_985a65b fill:#ffc;
```

How we should fork to stay in tune with each-other and easily accept improvements?

```mermaid
flowchart TD
    DIF --> |SpecUp_Daniel_Buchner| SpecUp_60ae636
    SpecUp_60ae636 --> |PR accepted| SpecUp_d392aa1
    SpecUp_d392aa1 --> |commit| SpecUp_e63f252
    SpecUp_d392aa1 --> |pull| ToIP_SpecUp_60ae636
    SpecUp_e63f252 --> |commit| SpecUp_985a65b
    SpecUp_60ae636 --> |Fork Specification Template| ToIP_SpecUp_60ae636
    ToIP_SpecUp_60ae636 --> |PR accepted| SpecUp_445a7db
    SpecUp_445a7db --> |fetch+merge| SpecUp_d392aa1
    SpecUp_445a7db --> |PR accepted| SpecUp_7667ec3
    SpecUp_7667ec3 -->  |Fork | Spec_kerific
    SpecUp_7667ec3 --> |Fork |keri-spec
    SpecUp_7667ec3 --> |Fork | acdc-spec
    SpecUp_445a7db --> |Fork | cesr-spec
    ToIP_SpecUp_60ae636 --> |Fork| trp-spec
    ToIP_SpecUp_60ae636 --> |Fork| tas-spec
    SpecUp_985a65b --> |fetch+merge| SpecUp_7667ec3
    SpecUp_7667ec3 --> |pull| SpecUp_985a65b

    style DIF fill:#ffc;
    style SpecUp_60ae636 fill:#ffc;
    style SpecUp_d392aa1 fill:#ffc;
    style SpecUp_e63f252 fill:#ffc;
    style SpecUp_985a65b fill:#ffc;
```
**Noticed the differences?**
1. Through *forking* instead of *copying* we keep git histories compatible
2. Through `fetch+merge` (or `pull` when no conflicts expected) we not only keep DIF and ToIP synced, but also it is very straightforward to update all the gh-pages-based specification websites that *use* the Specification Template to:
   - sync functionality and data
   - offer PRs from any of those installs


#### Roadmap to TEv2
As a TEv2 creator and frontman we share Rieks Joosten's viewpoint on this proposal for using Spec-Up refs and defs. 

He explained that the same features being discussed here were also added to TEv2. 

There is always tension between adding a lot of features and taking a long time, or keeping things very minimal. He pointed out that creating glossaries based on cherry-picking glossary entries based on personal preferences can be problematic because it doesn't actually establish shared understanding and criteria for defining terms.  
The larger the group involved, and the more varied their cultural backgrounds, the more problematic that can become. However, that doesn't mean we shouldn't start with tools that are actually working right now. Riek's personal preference is to use terminology that expresses the author's intentions clearly. For example, in reading the Spec-Up documentation, it was challenging for Rieks to understand it without more context.

Rieks would like to have several more sessions on TEv2 so we can still look at how we can use it for our terminology. He's not opposed to enhancing Spec-Up for these features, but at the same time keeping TEv2 tooling in progress. 

Rieks Joosten concluded that we need to see what tools are actually needed by both authors and readers to help them comprehend the terms they use. He can also explore how TEv2 tooling can be used to produce Spec-Up definitions.

Rieks Joosten was in favor of proceeding with changes to Spec-Up, but also to continue the work on TEv2 to tackle larger issues of terminology management.

#### TEv2 Explanation

##### Current structure
```mermaid
flowchart LR
A[A:Root];B[B:ScopeDir];C[/C:SAF/]; D[D:GlossaryDir]; E[E:CurTextDir]
    A -->|install| B
    B -->|config| C
    B -->|populate| D
    B -->|populate| E 
```

#### Docusaurus example CURRENT
```mermaid
flowchart LR
A[A:Root];B[B:/docs];C[/C:saf.yaml/]; D[D:glossaries]; E[E:terms]
    A -->|install| B
    B -->|create| C
    B -->|populate| D
    B -->|populate| E 
```
#### SpecUp example CURRENT
```mermaid
flowchart LR
A[A:Root];B[B:/spec];C[/C:saf.yaml/]; D[D:glossaries]; E[E:terms]
    A -->|install| B
    B -->|create| C
    B -->|populate| D
    B -->|populate| E 
```

##### Internal Scope Terminology - 0.1: no links & no classDef & no new forms
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    C --> D[/D:Curated text/]
    I -.-> two
    subgraph two[glossaries]
        M("`**MRG**`")
        Q(Q:HRG)
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]
    end
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
```

##### Internal Scope Terminology - 0.2: no links & no classDef & no styles
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    C --> D[/D:Curated text/]
    I -.-> two
    subgraph two[glossaries]
        M("`**MRG**`")
        Q(Q:HRG)
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]
    end
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
```

##### Internal Scope Terminology - 0.3: isolate - no subgraphs
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    C --> D[/D:Curated text/]
    I -.-> two
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
    end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
```

##### Internal Scope Terminology - 0.3.1: isolate - no comment
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    C --> D[/D:Curated text/]
    I -.-> two
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
```

##### Internal Scope Terminology - 0.3.2: isolate - no strange symbol
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]
    I -.-> two
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    B --> C((C:Scope ingress process))
```

##### Internal Scope Terminology - 0.3.3: isolate - no subgraphs!
```mermaid
flowchart LR
    H((H:Scope Admin process)) --> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]
    I -.-> two
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
```


##### Internal Scope Terminology - 0.4: isolate - all other strange stuff gone
```mermaid
flowchart LR
    H((H:Scope Admin process)) --> I[/I:SAF/]
    C --> D[/D:Curated text/]
    I -.-> two
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    B --> C((C:Scope ingress process))
```



##### Internal Scope Terminology - 1: no links & no classDef
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]
    I -.-> two
    subgraph two[glossaries]
        M("`**MRG**`")
        Q>Q:HRG]
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]
    end
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
```

##### Internal Scope Terminology - 2: no classDef
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)) --> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]
    I -.-> two
    subgraph two[glossaries]
        M("`**MRG**`")
        Q>Q:HRG]
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]
    end
    two --> E
    D --> E[E:mrgt]
    I -.-> E
    P[P:hrgt]
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]
    R -.-> N
    N -.-> R
    A[\A:Raw text\] --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process))
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
click J href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrg-import" "Open this in a new tab" _blank
click E href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrgt" "Open this in a new tab" _blank
click P href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/hrgt" "Open this in a new tab" _blank
click N href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/trrt" "Open this in a new tab" _blank
```

##### Internal Scope Terminology - 3 : no links
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)):::armyGreenFill --> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]:::lightYellowFill
    I -.-> two
    subgraph two[glossaries]
        M("`**MRG**`")
        Q>Q:HRG]
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]:::medGreenFill
    end
    two --> E
    D --> E[E:mrgt]:::medGreenFill
    I -.-> E
    P[P:hrgt]:::medGreenFill
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
 end
    two -.-> |has a| R[\R:Formatted text\]:::lightYellowFill
    R -.-> N
    N -.-> R
    A[\A:Raw text\]:::lightYellowFill --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process)):::armyGreenFill
classDef lightYellowFill fill:#ff9,stroke:#333,stroke-width:3px
classDef medGreenFill fill:#0c3,stroke:#333,stroke-width:3px
classDef armyGreenFill fill:#9c6,stroke:#333,stroke-width:3px
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
```

##### Internal Scope Terminology
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)):::armyGreenFill --> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]:::lightYellowFill
    I -.-> two
    subgraph two[glossaries]
        M("`**MRG**`")
        Q>Q:HRG]
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]:::medGreenFill
    end
    two --> E
    D --> E[E:mrgt]:::medGreenFill
    I -.-> E
    P[P:hrgt]:::medGreenFill
    E --> two
    two --> P
    P --> two
    two --> N
    two --> Q
    end
    two -.-> |has a| R[\R:Formatted text\]:::lightYellowFill
    R -.-> N
    N -.-> R
    A[\A:Raw text\]:::lightYellowFill --> B[B: Ingress toolbox]
    B --> C((C:Scope ingress process)):::armyGreenFill
classDef lightYellowFill fill:#ff9,stroke:#333,stroke-width:3px
classDef medGreenFill fill:#0c3,stroke:#333,stroke-width:3px
classDef armyGreenFill fill:#9c6,stroke:#333,stroke-width:3px
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
click J href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrg-import" "Open this in a new tab" _blank
click E href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrgt" "Open this in a new tab" _blank
click P href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/hrgt" "Open this in a new tab" _blank
click N href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/trrt" "Open this in a new tab" _blank
```

##### External glossary import
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)):::armyGreenFill--> I[/I:SAF/]
    %% X ~~~~ H
    C --> D[/D:Curated text/]:::lightYellowFill
    I -.-> two
    I -.-> J[J:MRG Importer]:::medGreenFill
    subgraph two[glossaries]
        K>MRG]:::lightBlueFill; L>MRG]:::violetFill
        M("`**MRG**`")
        Q>Q:HRG]
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]:::medGreenFill
    end
    J --> two
    two --> E
    D --> E[E:mrgt]:::medGreenFill
    I -.-> E
    P[P:hrgt]:::medGreenFill
    E --> two
    two --> P
    two --> N
    two --> Q
 end
    I -.-> three
    I -.-> four
    W --> J
    WW --> J
    WWW ~~~ J
    two -.-> |has a| R[\R:Formatted text\]:::lightYellowFill
    R -.-> N
    N -.-> R
    A[\A:Raw text\]:::lightYellowFill --> B[B:Ingress toolbox]
    B --> C((C:Scope ingress process)):::armyGreenFill   
   subgraph three[Scope Dir]
   V[/SAF/] ~~~ W[MRG]:::lightBlueFill
   end
   subgraph four[Scope Dir]
   VV[/SAF/] ~~~ WW[MRG]:::violetFill
   end
    subgraph five[Scope Dir]
   VVV[/SAF/] ~~~ WWW[MRG]:::lightRedFill
   end
classDef lightYellowFill fill:#ff9,stroke:#333,stroke-width:3px
classDef medGreenFill fill:#0c3,stroke:#333,stroke-width:3px
classDef armyGreenFill fill:#9c6,stroke:#333,stroke-width:3px
classDef lightBlueFill fill:#9cf,stroke:#333,stroke-width:3px
classDef violetFill fill:#99f,stroke:#333,stroke-width:3px
classDef lightRedFill fill:#c00,stroke:#333,stroke-width:3px
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style three fill:#69f,stroke:#333,stroke-width:1px
style four fill:#60c,stroke:#333,stroke-width:1px
style five fill:#c30,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
click J href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrg-import" "Open this in a new tab" _blank
click E href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrgt" "Open this in a new tab" _blank
click P href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/hrgt" "Open this in a new tab" _blank
click N href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/trrt" "Open this in a new tab" _blank
```

##### Full architecture
```mermaid
flowchart LR
    subgraph one [SCOPE DIRECTORY]
    H((H:Scope Admin process)):::armyGreenFill--> I[/I:SAF/]
    C --> D[/D:Curated text/]:::lightYellowFill
    I -.-> two
    I -.-> J[J:MRG Importer]:::medGreenFill
    subgraph two[📂 glossaries]
        K>MRG]:::lightBlueFill; L>MRG]:::violetFill
        M("`**MRG**`")
        Q>Q:HRG]
    end
    subgraph seven[3rd party rendering tools]
        N[N:trrt]:::medGreenFill
    end
    S[S:Integrity Checker Tool]:::medGreenFill
    J --> K
    J --> L
    K --> E
    L --> E
    D --> E[E:mrgt]:::medGreenFill
    I -.-> E
    P[P:hrgt]:::medGreenFill
    E --> M
    M --> P
    M --> N
    P --> Q
 end
    I -.-> three
    I -.-> four
    W --> J
    WW --> J
    WWW ~~~ J
    Q -.-> |is a| R[\R:Formatted text\]:::lightYellowFill
    R -.-> N
    N -.-> R
    A[\A:Raw text\]:::lightYellowFill --> B[B: 🧰 Ingress toolbox]
    B --> C((C:Scope ingress process)):::armyGreenFill  
   subgraph three[Scope Dir]
   V[/SAF/] ~~~ W[MRG]:::lightBlueFill
   end
   subgraph four[Scope Dir]
   VV[/SAF/] ~~~ WW[MRG]:::violetFill
   end
    subgraph five[Scope Dir]
   VVV[/SAF/] ~~~ WWW[MRG]:::lightRedFill
   end

classDef lightYellowFill fill:#ff9,stroke:#333,stroke-width:3px
classDef medGreenFill fill:#0c3,stroke:#333,stroke-width:3px
classDef armyGreenFill fill:#9c6,stroke:#333,stroke-width:3px
classDef lightBlueFill fill:#9cf,stroke:#333,stroke-width:3px
classDef violetFill fill:#99f,stroke:#333,stroke-width:3px
classDef lightRedFill fill:#c00,stroke:#333,stroke-width:3px
style B fill:#336,stroke:#f66,stroke-width:2px,color:#fff,stroke-dasharray: 5 5
style one fill:#ff3,stroke:#333,stroke-width:1px
style two fill:#fc6,stroke:#333,stroke-width:1px
style three fill:#69f,stroke:#333,stroke-width:1px
style four fill:#60c,stroke:#333,stroke-width:1px
style five fill:#c30,stroke:#333,stroke-width:1px
style seven fill:#ff9,stroke:#333,stroke-width:1px
click J href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrg-import" "Open this in a new tab" _blank
click E href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/mrgt" "Open this in a new tab" _blank
click P href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/hrgt" "Open this in a new tab" _blank
click S href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools-envisaged/ict" "Open this in a new tab" _blank
click N href "https://tno-terminology-design.github.io/tev2-specifications/docs/specs/tools/trrt" "Open this in a new tab" _blank
```

#### Always archive never delete

Darrell O'Donnell clarified that technical maintainers we will not delete any ToIP repos, but will only archive them.

| TBW |