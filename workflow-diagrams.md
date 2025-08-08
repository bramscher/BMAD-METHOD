# BMAD-METHOD Workflow Diagrams

## 1. Core Planning Workflow

```mermaid
graph TD
    A["Start: Project Idea"] --> B{"Optional: Analyst Brainstorming"}
    B -->|Yes| C["Analyst: Market Research & Analysis"]
    B -->|No| D["Create Project Brief"]
    C --> D["Analyst: Create Project Brief"]
    D --> E["PM: Create PRD from Brief"]
    E --> F["Architect: Create Architecture from PRD"]
    F --> G["PO: Run Master Checklist"]
    G --> H{"Documents Aligned?"}
    H -->|Yes| I["Planning Complete"]
    H -->|No| J["PO: Update Epics & Stories"]
    J --> K["Update PRD/Architecture as needed"]
    K --> G
    I --> L["📁 Switch to IDE"]
    L --> M["PO: Shard Documents"]
    M --> N["Ready for SM/Dev Cycle"]

    style I fill:#34a853,color:#fff
    style G fill:#f9ab00,color:#fff
    style L fill:#1a73e8,color:#fff
    style N fill:#34a853,color:#fff
```

## 2. Core Development Cycle

```mermaid
graph TD
    A["Start: Planning Artifacts Complete"] --> B["PO: Shard Epics"]
    B --> C["PO: Shard Arch"]
    C --> D["Development Phase"]
    D --> E["Scrum Master: Drafts next story from sharded epic"]
    E --> F{"User Approval"}
    F -->|Approved| G["Dev: Implement Story"]
    F -->|Needs Changes| E
    G --> H["Dev: Complete story Tasks"]
    H --> I["Dev: Mark Ready for Review"]
    I --> J{"User Verification"}
    J -->|Request QA Review| K["QA: Run review-story task"]
    J -->|Approve Without QA| M["Mark Story as Done"]
    K --> L{"QA Review Results"}
    L -->|Needs Work| G
    L -->|Approved| M["Mark Story as Done"]
    J -->|Needs Fixes| G
    M --> E

    style M fill:#34a853,color:#fff
    style K fill:#f9ab00,color:#fff
```

## 3. Greenfield Fullstack Workflow

```mermaid
graph TD
    A[Start: Greenfield Project] --> B[analyst: project-brief.md]
    B --> C[pm: prd.md]
    C --> D[ux-expert: front-end-spec.md]
    D --> D2{Generate v0 prompt?}
    D2 -->|Yes| D3[ux-expert: create v0 prompt]
    D2 -->|No| E[architect: fullstack-architecture.md]
    D3 --> D4[User: generate UI in v0/Lovable]
    D4 --> E
    E --> F{Architecture suggests PRD changes?}
    F -->|Yes| G[pm: update prd.md]
    F -->|No| H[po: validate all artifacts]
    G --> H
    H --> I{PO finds issues?}
    I -->|Yes| J[Return to relevant agent for fixes]
    I -->|No| K[po: shard documents]
    J --> H
    
    K --> L[sm: create story]
    L --> M{Review draft story?}
    M -->|Yes| N[analyst/pm: review & approve story]
    M -->|No| O[dev: implement story]
    N --> O
    O --> P{QA review?}
    P -->|Yes| Q[qa: review implementation]
    P -->|No| R{More stories?}
    Q --> S{QA found issues?}
    S -->|Yes| T[dev: address QA feedback]
    S -->|No| R
    T --> Q
    R -->|Yes| L
    R -->|No| U{Epic retrospective?}
    U -->|Yes| V[po: epic retrospective]
    U -->|No| W[Project Complete]
    V --> W

    B -.-> B1[Optional: brainstorming]
    B -.-> B2[Optional: market research]
    D -.-> D1[Optional: user research]
    E -.-> E1[Optional: technical research]

    style W fill:#90EE90
    style K fill:#ADD8E6
    style L fill:#ADD8E6
    style O fill:#ADD8E6
    style D3 fill:#E6E6FA
    style D4 fill:#E6E6FA
    style B fill:#FFE4B5
    style C fill:#FFE4B5
    style D fill:#FFE4B5
    style E fill:#FFE4B5
    style N fill:#F0E68C
    style Q fill:#F0E68C
    style V fill:#F0E68C
```

## 4. Greenfield UI Workflow

```mermaid
graph TD
    A[Start: UI Development] --> B[analyst: project-brief.md]
    B --> C[pm: prd.md]
    C --> D[ux-expert: front-end-spec.md]
    D --> D2{Generate v0 prompt?}
    D2 -->|Yes| D3[ux-expert: create v0 prompt]
    D2 -->|No| E[architect: front-end-architecture.md]
    D3 --> D4[User: generate UI in v0/Lovable]
    D4 --> E
    E --> F{Architecture suggests PRD changes?}
    F -->|Yes| G[pm: update prd.md]
    F -->|No| H[po: validate all artifacts]
    G --> H
    H --> I{PO finds issues?}
    I -->|Yes| J[Return to relevant agent for fixes]
    I -->|No| K[po: shard documents]
    J --> H
    
    K --> L[sm: create story]
    L --> M{Review draft story?}
    M -->|Yes| N[analyst/pm: review & approve story]
    M -->|No| O[dev: implement story]
    N --> O
    O --> P{QA review?}
    P -->|Yes| Q[qa: review implementation]
    P -->|No| R{More stories?}
    Q --> S{QA found issues?}
    S -->|Yes| T[dev: address QA feedback]
    S -->|No| R
    T --> Q
    R -->|Yes| L
    R -->|No| U{Epic retrospective?}
    U -->|Yes| V[po: epic retrospective]
    U -->|No| W[Project Complete]
    V --> W

    B -.-> B1[Optional: brainstorming]
    B -.-> B2[Optional: market research]
    D -.-> D1[Optional: user research]
    E -.-> E1[Optional: technical research]

    style W fill:#90EE90
    style K fill:#ADD8E6
    style L fill:#ADD8E6
    style O fill:#ADD8E6
    style D3 fill:#E6E6FA
    style D4 fill:#E6E6FA
    style B fill:#FFE4B5
    style C fill:#FFE4B5
    style D fill:#FFE4B5
    style E fill:#FFE4B5
    style N fill:#F0E68C
    style Q fill:#F0E68C
    style V fill:#F0E68C
```

## 5. Brownfield Fullstack Enhancement

```mermaid
graph TD
    A[Start: Brownfield Enhancement] --> B[analyst: classify enhancement scope]
    B --> C{Enhancement Size?}
    
    C -->|Single Story| D[pm: brownfield-create-story]
    C -->|1-3 Stories| E[pm: brownfield-create-epic]
    C -->|Major Enhancement| F[analyst: check documentation]
    
    D --> END1[To Dev Implementation]
    E --> END2[To Story Creation]
    
    F --> G{Docs Adequate?}
    G -->|No| H[architect: document-project]
    G -->|Yes| I[pm: brownfield PRD]
    H --> I
    
    I --> J{Architecture Needed?}
    J -->|Yes| K[architect: architecture.md]
    J -->|No| L[po: validate artifacts]
    K --> L
    
    L --> M{PO finds issues?}
    M -->|Yes| N[Fix issues]
    M -->|No| O[po: shard documents]
    N --> L
    
    O --> P[sm: create story]
    P --> Q{Story Type?}
    Q -->|Sharded PRD| R[create-next-story]
    Q -->|Brownfield Docs| S[create-brownfield-story]
    
    R --> T{Review draft?}
    S --> T
    T -->|Yes| U[review & approve]
    T -->|No| V[dev: implement]
    U --> V
    
    V --> W{QA review?}
    W -->|Yes| X[qa: review]
    W -->|No| Y{More stories?}
    X --> Z{Issues?}
    Z -->|Yes| AA[dev: fix]
    Z -->|No| Y
    AA --> X
    Y -->|Yes| P
    Y -->|No| AB{Retrospective?}
    AB -->|Yes| AC[po: retrospective]
    AB -->|No| AD[Complete]
    AC --> AD

    style AD fill:#90EE90
    style END1 fill:#90EE90
    style END2 fill:#90EE90
    style D fill:#87CEEB
    style E fill:#87CEEB
    style I fill:#FFE4B5
    style K fill:#FFE4B5
    style O fill:#ADD8E6
    style P fill:#ADD8E6
    style V fill:#ADD8E6
    style U fill:#F0E68C
    style X fill:#F0E68C
    style AC fill:#F0E68C
```

## 6. Game Development Workflow

```mermaid
graph TD
    A[Start: Game Development Project] --> B{Project Scope?}
    B -->|Full Game/Production| C[game-designer: game-brief.md]
    B -->|Prototype/Game Jam| D[game-designer: focused game-brief.md]

    C --> E[game-designer: game-design-doc.md]
    E --> F[game-designer: level-design-doc.md]
    F --> G[solution-architect: game-architecture.md]
    G --> H[game-designer: validate design consistency]
    H --> I{Design validation issues?}
    I -->|Yes| J[Return to relevant agent for fixes]
    I -->|No| K[Set up game project structure]
    J --> H
    K --> L[Move to Story Development Phase]

    D --> M[game-designer: prototype-design.md]
    M --> N[Move to Rapid Implementation]

    C -.-> C1[Optional: brainstorming]
    C -.-> C2[Optional: game research]
    E -.-> E1[Optional: competitive analysis]
    F -.-> F1[Optional: level prototyping]
    G -.-> G1[Optional: technical research]
    D -.-> D1[Optional: quick brainstorming]

    style L fill:#90EE90
    style N fill:#90EE90
    style C fill:#FFE4B5
    style E fill:#FFE4B5
    style F fill:#FFE4B5
    style G fill:#FFE4B5
    style D fill:#FFB6C1
    style M fill:#FFB6C1
```

## How to Preview These Diagrams

1. **Open this file** (`workflow-diagrams.md`) in Cursor
2. **Right-click on any mermaid code block** and select "Open Preview" or "Preview Mermaid"
3. **Or use the command palette**: `Cmd+Shift+P` → "Mermaid: Preview"
4. **Or install additional Mermaid extensions** if needed:
   - "Mermaid Markdown Syntax Highlighting"
   - "Mermaid Preview"

## Alternative Methods

### Using Live Server
If you want to see the diagrams in a browser:
1. Install the "Live Server" extension (you already have it)
2. Right-click on this markdown file
3. Select "Open with Live Server"
4. The diagrams will render in your browser

### Using GitHub
You can also view these diagrams directly on GitHub, as GitHub natively supports Mermaid diagrams in markdown files. 